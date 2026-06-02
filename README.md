# amalgame-hardware-comms

Portable **serial-comms drivers** for Amalgame over the [`amalgame-hal`](https://github.com/amalgame-lang/amalgame-hal) `SerialPort` interface. v0.1 ships an NMEA-0183 **GPS** parser — for trackers, drones, data loggers.

```sh
amc package add hardware-comms
```

```amalgame
import Amalgame.Hardware          // Uart (Pi backend)
import Amalgame.Hardware.Comms

let gps = new Gps(new Uart("/dev/serial0", 9600))
// loop:
gps.Update()
if (gps.HasFix()) {
    Console.WriteLine(String_FromFloat(gps.Latitude()) + ", " + String_FromFloat(gps.Longitude()))
}
```

| Class | API |
|---|---|
| `Gps(port: SerialPort)` | `Update()`, `HasFix()`, `Latitude()`, `Longitude()`, `Altitude()`, `Satellites()` |

Requires amc ≥ 0.8.72. Apache-2.0.
