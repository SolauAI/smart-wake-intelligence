# iOS Architecture

The iPhone is the final alarm endpoint and is intentionally placed away from the bed.

iOS does not permit arbitrary unrestricted continuous app processing overnight. Core Bluetooth supports BLE communication with background behavior subject to iOS lifecycle rules.

https://developer.apple.com/documentation/corebluetooth

Prefer:
Garmin/watch-side event -> approved phone communication -> iOS app -> reliable local alarm mechanism

over:
iPhone continuously polling Garmin data all night.

The alarm layer must maintain:
- hard fallback alarm;
- candidate wake deadline;
- cancellation/rescheduling rules;
- persistence across suspension/relaunch;
- clear state transitions.

R&D questions:
1. Which Apple alarm/notification mechanism provides the required audible reliability?
2. Can an adaptive alarm be scheduled/rescheduled sufficiently close to wake time?
3. What happens if the app is terminated?
4. What happens if Focus, silent mode or permissions interfere?
5. Can current iOS background Bluetooth mechanisms materially improve reliability?
