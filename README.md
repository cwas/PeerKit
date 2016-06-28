# PeerPack

## An open source Swift framework for building event-driven, zero-config Multipeer Connectivity apps

PeerPack has been forked and refactored from [PeerKit](https://github.com/jpsim/PeerKit) for use in [Fog Machine](https://github.com/ngageoint/fog-machine).

## Usage

```swift
// Automatically detect and connect to other peers with specified service type
// Service type can contain only ASCII lowercase letters, numbers, and hyphens.
// It must be a unique string, at most 15 characters long
// Note: Devices will only connect to other devices with the same service type value.
let SERVICE_TYPE = "FM" + "UniqueId123"
PeerPack.transceiver.startTransceiving(serviceType: SERVICE_TYPE)


// When a peer connects
PeerPack.onConnect = { (myPeerID: MCPeerID, peerID: MCPeerID) -> Void in
    // Handle onConnect
}


// When a peer disconnects
PeerPack.onDisconnect = { (myPeerID: MCPeerID, peerID: MCPeerID) -> Void in
    // Handle onDisconnect
}


// When a work request comes over the air
PeerPack.eventBlocks[self.sendWorkEvent + String(fmTool.id())] = { (fromPeerID: MCPeerID, object: AnyObject?) -> Void in
    // Process work
}

// When a work request is sent
PeerPack.sendEvent("sendWorkEvent", object: NSKeyedArchiver.archivedDataWithRootObject(data), toPeers: [mcPeerID])
```

Reference the [Fog Machine](https://github.com/ngageoint/fog-machine) app for an example of how the Fog Machine framework uses PeerPack and two example apps which use the Fog Machine framework. The [FogMachine.swift](https://github.com/ngageoint/fog-machine/blob/master/FogMachine/FogMachine/FogMachine.swift) file handles all PeerPack usage.

## License

This project is under the MIT license.

## Acknowledgements

PeerPack was forked from the below open source project:
- **PeerKit**  
*https://github.com/jpsim/PeerKit*
This product includes software licensed under the MIT License http://opensource.org/licenses/mit-license.php