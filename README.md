Demonstrates a bug in com.android.tools.build:gradle:2.1.0. After cleaning and building, a rebuild without changes recompiles. See [log1.txt](log1.txt) and [log2.txt](log2.txt) or run the following:

```
./gradlew clean
./gradlew assembleDebug --info
./gradlew assembleDebug --info
```

In the second log you will see the following:

```
Executing task ':library1:incrementalDebugJavaCompilationSafeguard' (up-to-date check took 0.002 secs) due to:
  Input file /Users/nickd/Development/android-rebuild-bug/library1/build/generated/source/r/debug/com/squareup/helloworld/library1/R.java has been added.
  Input file /Users/nickd/Development/android-rebuild-bug/library1/build/generated/source/r/debug/com has been added.
  Input file /Users/nickd/Development/android-rebuild-bug/library1/build/generated/source/r/debug/com/squareup has been added.

...

Executing task ':library1:compileDebugJavaWithJavac' (up-to-date check took 0.004 secs) due to:
  Output file /Users/nickd/Development/android-rebuild-bug/library1/build/intermediates/classes/debug has changed.
  Output file /Users/nickd/Development/android-rebuild-bug/library1/build/intermediates/classes/debug/com/squareup/helloworld/library1/R$attr.class has been removed.
  Output file /Users/nickd/Development/android-rebuild-bug/library1/build/intermediates/classes/debug/com/squareup/helloworld/library1/R.class has been removed.
```
