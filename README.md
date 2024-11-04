# Unreal Multiuser Session Commands
These commands will allow someone to start an Unreal Multiuser server and then join the session from an editor and from a render node. Just run 1 command after the other in a PowerShell window.

## Simplified

### Multiuser Server
```powershell
& "C:\Program Files\Epic Games\UE_5.4\Engine\Binaries\Win64\UnrealMultiUserSlateServer.exe" -CONCERTSERVER="unrealMUS" -UDPMESSAGING_SHARE_KNOWN_NODES=1 -UDPMESSAGING_TRANSPORT_UNICAST="127.0.0.1:9030" -UDPMESSAGING_TRANSPORT_MULTICAST="230.0.0.1:6666" -messaging
```

### Editor
```powershell
& "C:\Program Files\Epic Games\UE_5.4\Engine\Binaries\Win64\UnrealEditor.exe" "C:\Users\dostr\Documents\Unreal Projects\gitSwitchboard\gitSwitchboard.uproject" /Game/Main Log=Editor_1.log -CONCERTRETRYAUTOCONNECTONERROR -CONCERTAUTOCONNECT -CONCERTSERVER="unrealMUS" -CONCERTSESSION="Session_1" -CONCERTDISPLAYNAME="Editor_1" -StageFriendlyName="Editor_1" -DPCVars="Slate.bAllowThrottling=0" -ConcertReflectVisibility=1 -UDPMESSAGING_TRANSPORT_MULTICAST="230.0.0.1:6666" -UDPMESSAGING_TRANSPORT_UNICAST="127.0.0.1:0" -UDPMESSAGING_TRANSPORT_STATIC="127.0.0.1:9030"
```

### Node
```powershell
& "C:\Program Files\Epic Games\UE_5.4\Engine\Binaries\Win64\UnrealEditor.exe" "C:\Users\dostr\Documents\Unreal Projects\gitSwitchboard\gitSwitchboard.uproject" -game /Game/Main -messaging -nosplash -fixedseed -NoVerifyGC -noxrstereo -xrtrackingonly -StageFriendlyName="Node_0" -MaxGPUCount=2 -dx12 -nosound Log=Node_0.log -UDPMESSAGING_TRANSPORT_MULTICAST="230.0.0.1:6666" -UDPMESSAGING_TRANSPORT_UNICAST="127.0.0.1:0" -UDPMESSAGING_TRANSPORT_STATIC="127.0.0.1:9030" -ExecCmds="DisableAllScreenMessages" -windowed -forceres WinX=0 WinY=0 ResX=1920 ResY=1080 -CONCERTRETRYAUTOCONNECTONERROR -CONCERTAUTOCONNECT -CONCERTSERVER="unrealMUS" -CONCERTSESSION="Session_1" -CONCERTDISPLAYNAME="Node_0" -CONCERTISHEADLESS
```

## Switchboard

### Multiuser Server
```powershell
& "C:\Program Files\Epic Games\UE_5.4\Engine\Binaries\Win64\UnrealMultiUserSlateServer.exe" -CONCERTSERVER="unrealMUS_Z6rbx5k3poEP" -UDPMESSAGING_SHARE_KNOWN_NODES=1 -UDPMESSAGING_TRANSPORT_UNICAST="127.0.0.1:9030" -UDPMESSAGING_TRANSPORT_MULTICAST="230.0.0.1:6666" -Messaging
```

### Editor
```powershell
& "C:\Program Files\Epic Games\UE_5.4\Engine\Binaries\Win64\UnrealEditor.exe" "C:\Users\dostr\Documents\Unreal Projects\gitSwitchboard\gitSwitchboard.uproject" /Game/Main Log=Editor_1.log -CONCERTRETRYAUTOCONNECTONERROR -CONCERTAUTOCONNECT -CONCERTSERVER="unrealMUS_Z6rbx5k3poEP" -CONCERTSESSION="Session_1" -CONCERTDISPLAYNAME="Editor_1" -StageFriendlyName="Editor_1" -DPCVars="Slate.bAllowThrottling=0" -ConcertReflectVisibility=1 -UDPMESSAGING_TRANSPORT_MULTICAST="230.0.0.1:6666" -UDPMESSAGING_TRANSPORT_UNICAST="127.0.0.1:0" -UDPMESSAGING_TRANSPORT_STATIC="127.0.0.1:9030" -ini:Engine:[/Script/ConcertTakeRecorder.ConcertSessionRecordSettings]:LocalSettings="(bRecordOnClient=True)"
```

### Node
```powershell
& "C:\Program Files\Epic Games\UE_5.4\Engine\Binaries\Win64\UnrealEditor.exe" "C:\Users\dostr\Documents\Unreal Projects\gitSwitchboard\gitSwitchboard.uproject" -game /Game/Main -messaging -dc_cluster -nosplash -fixedseed -NoVerifyGC -noxrstereo -xrtrackingonly -RemoteControlIsHeadless -StageFriendlyName="Node_0" -MaxGPUCount=2 -dc_cfg="C:\Users\dostr\AppData\Local\Temp\ndisplay\193AA743475B483FF5E9D99A004DBCF8.ndisplay" -dx12 -dc_dev_mono -nosound -dc_node=Node_0 Log=Node_0.log -ini:Engine:[/Script/Engine.Engine]:GameEngine=/Script/DisplayCluster.DisplayClusterGameEngine,[/Script/Engine.Engine]:GameViewportClientClassName=/Script/DisplayCluster.DisplayClusterViewportClient,[/Script/Engine.UserInterfaceSettings]:bAllowHighDPIInGameMode=True -ini:Game:[/Script/EngineSettings.GeneralProjectSettings]:bUseBorderlessWindow=True -ini:Input:[/Script/Engine.InputSettings]:DefaultPlayerInputClass=/Script/DisplayCluster.DisplayClusterPlayerInput -unattended -NoScreenMessages -handleensurepercent=0 -UDPMESSAGING_TRANSPORT_MULTICAST="230.0.0.1:6666" -UDPMESSAGING_TRANSPORT_UNICAST="127.0.0.1:0" -UDPMESSAGING_TRANSPORT_STATIC="127.0.0.1:9030" -ExecCmds="DisableAllScreenMessages" -windowed -forceres WinX=0 WinY=0 ResX=1920 ResY=1080 -CONCERTRETRYAUTOCONNECTONERROR -CONCERTAUTOCONNECT -CONCERTSERVER="unrealMUS_Z6rbx5k3poEP" -CONCERTSESSION="Session_1" -CONCERTDISPLAYNAME="Node_0" -CONCERTISHEADLESS -DPCVars="Slate.bAllowNotifications=0,p.Chaos.Solver.Deterministic=1,LevelInstance.ForceEditorWorldMode=1"
```