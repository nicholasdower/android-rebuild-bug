Demonstrates a bug in com.android.tools.build:gradle:2.1.0. Run the following:
```
./gradlew clean
./gradlew assembleDebug
# This should be a noop but isn't.
./gradlew assembleDebug
```
