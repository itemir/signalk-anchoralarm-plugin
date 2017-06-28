# signalk-anchoralarm-plugin
SignalK Node Server Anchor Alarm Plugin

To install, cd to your signalk-node-server directory and run:

```
npm install signalk-anchoralarm-plugin
```

Then go to http://localhost:3000/plugins and enable the anchar alarm plugin.

Then use WilhelmSK to set the alarm (https://itunes.apple.com/us/app/wilhelmsk/id1150499484?mt=8)

If not using WilhelmSK, you can setup the alarm using the REST API.

When you drop the anchor in the water, Call dropAnchor:


```
curl -X POST -H "Content-Type: application/json" -d '{}' http://localhost:3000/plugins/anchoralarm/dropAnchor
```

After you have let the anchor rode out, call setRadius. This will calculate and set the alarm radius.

```
curl -X POST -H "Content-Type: application/json" -d '{}' http://localhost:3000/plugins/anchoralarm/setRadius
```

You can adjust the radius (in meters) via:

```
curl -X POST -H "Content-Type: application/json" -d '{"radius": 30}' http://localhost:3000/plugins/anchoralarm/setRadius
```

When you raise the anchor, call raiseAnchor.

```
curl -X POST -H "Content-Type: application/json" -d '{}' http://localhost:3000/plugins/anchoralarm/raiseAnchor
```

If you need to set the anchor position after you have already let the rode out, it can esitmate the andchor position based on heading, depth and rode length:

```
curl -X POST -H "Content-Type: application/json" -d '{"anchorDepth": 3, "rodeLength":30}' http://localhost:3000/plugins/anchoralarm/setManualAnchor
```
