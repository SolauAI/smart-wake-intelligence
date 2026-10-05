# Garmin Architecture

## Official integration options

Garmin Health API exposes all-day health data including sleep, heart rate, stress, respiration and Body Battery. Data become available after device sync to Garmin Connect. Commercial use requires Garmin program/licensing arrangements.

https://developer.garmin.com/gc-developer-program/health-api/

Garmin Health SDKs are enterprise-oriented and support real-time streaming/configurable logged data, with commercial licensing requirements.

https://developer.garmin.com/health-sdk/
https://developer.garmin.com/health-sdk/questions-answers/

Connect IQ apps can communicate with a phone over BLE through Toybox.Communications. Background services exist but can be constrained or terminated.

https://developer.garmin.com/connect-iq/api-docs/Toybox/Communications.html
https://developer.garmin.com/connect-iq/articles/core-topics/Backgrounding.html
https://developer.garmin.com/connect-iq/api-docs/Toybox/System/ServiceDelegate.html

## Architectural consequence
Do not assume Garmin Connect cloud data can provide sufficiently low-latency night data for a consumer real-time alarm.

Investigate two tracks:
A. Connect IQ companion architecture where the watch participates directly in the night decision and sends compact events to iPhone.
B. Garmin Health SDK / licensed enterprise architecture if real-time access is required.

## Constraints
Background services can be time/event driven and may be terminated. BLE bandwidth is limited. Prefer compact features/events over raw streaming.

## Critical R&D questions
1. Can the target Garmin model expose the required overnight signals to Connect IQ?
2. Can the watch execute the required inference during the target night?
3. Can it reliably notify the iPhone at the chosen wake moment?
4. What happens when the watch is disconnected?
5. Which Garmin model(s) are supported for V1?
