# Supported commands

Not all commands in the [`flutter`](https://flutter.dev/docs/reference/flutter-cli) CLI are supported by `flutter-tizen`.

## Global options

- ### `-d`, `--device-id`

  Specify the target device ID. The tool finds a connected device automatically if not specified.

  ```sh
  flutter-tizen [command] -d emulator-26101
  ```

- ### `-v`, `--verbose`

  Show verbose output.

  ```sh
  flutter-tizen [command] -v
  ```

## Commands and examples

- ### `analyze`

  Analyze the current project's Dart source code. Identical to `flutter analyze`.

  ```sh
  flutter-tizen analyze
  ```

- ### `attach`

  Attach to a Flutter app running on a Tizen device.

  ```sh
  flutter-tizen attach
  ```

- ### `build`

  Flutter build command. See `flutter-tizen build -h` for subcommands.

  ```sh
  # Build a TPK without installing on a device.
  flutter-tizen build tpk

  # Build for a TV device.
  flutter-tizen build tpk --device-profile tv

  # Build for an emulator.
  flutter-tizen build tpk --debug --target-arch x86
  ```

- ### `clean`

  Remove the current project's build artifacts and intermediate files.

  ```sh
  flutter-tizen clean
  ```

- ### `config`

  Configure Flutter settings. Identical to `flutter config`.

  ```sh
  # Enable Flutte for web. This takes effect globally.
  flutter-tizen config --enable-web
  ```

- ### `create`

  Create a new project.

  ```sh
  # Create a new app project in the current directory.
  # If a project already exists in the current directory, only missing files are added.
  flutter-tizen create .

  # The Tizen embedding APIs are not yet stable.
  # Delete and re-create the `tizen` directory as often as you can.
  rm -r tizen/
  flutter-tizen create .

  # Create a new plugin project in `foobar_tizen` directory.
  flutter-tizen create --template plugin --org com.example foobar_tizen
  ```

- ### `devices`

  List all connected devices.

  ```sh
  flutter-tizen devices
  ```

- ### `doctor`

  Show information about the installed Tizen tooling.

  ```sh
  flutter-tizen doctor
  ```

- ### `drive`

  Run Flutter Driver tests. For details, see [`integration_test`](https://github.com/flutter/plugins/tree/master/packages/integration_test) (plugin).

  ```sh
  # Launch `foo_test.dart` on a Tizen device.
  flutter-tizen drive --driver=test_driver/integration_test.dart --target=integration_test/foo_test.dart
  ```

- ### `emulators`

  List and launch emulators. Currently only works with Tizen emulators.

  ```sh
  # List all emulator instances.
  flutter-tizen emulators

  # Launch a TV 5.5 emulator.
  flutter-tizen emulators --launch T-samsung-5.5-x86
  ```

- ### `format`

  Format Dart files. Identical to `flutter format`.

  ```sh
  flutter-tizen format foo.dart
  ```

- ### `gen-l10n`

  Generate localizations for the Flutter project. Identical to `flutter gen-l10n`.

  ```sh
  # Note: Create a template arb file "app_en.arb" in "lib/l10n" before running this.
  flutter-tizen gen-l10n
  ```

- ### `install`

  Install TPK on a Tizen device.

  ```sh
  # Install `build/tizen/*.tpk` on a Tizen device.
  flutter-tizen install

  # Uninstall if already installed.
  flutter-tizen install --uninstall-only
  ```

- ### `logs`

  Show the device log output associated with running Flutter apps.

  ```sh
  flutter-tizen logs
  ```

- ### `pub`

  Commands for managing Flutter packages. Identical to `flutter pub`.

  ```sh
  # Get packages for the current project.
  flutter-tizen pub get
  ```

- ### `run`

  Build the current project and run on a Tizen device.

  ```sh
  # Build and run in debug mode.
  flutter-tizen run

  # Build and run in release mode.
  # Full performance, but no debugging (hot-reload) support.
  flutter-tizen run --release

  # Specify the device ID to run on.
  flutter-tizen run -d emulator-26101
  ```

- ### `screenshot`

  Take a screenshot from a connected device.

  ```sh
  flutter-tizen screenshot --type rasterizer --observatory-uri http://127.0.0.1:43000/Swm0bjIe0ks=
  ```

  You have to specify both `--type` and `--observatory-uri` values because the default (`device`) screenshot type is not supported by Tizen devices. The observatory URI value can be found in the device log output (`flutter-tizen run` or `flutter-tizen logs`) after you start an app in debug or profile mode.

- ### `symbolize`

  Symbolize a stack trace from a Flutter app which has been built with the `--split-debug-info` option.

  ```sh
  flutter-tizen symbolize --debug-info app.android-arm.symbols --input stack_trace.err
  ```

- ### `test`

  Run tests in this package.

  ```sh
  flutter-tizen test test/general
  ```
