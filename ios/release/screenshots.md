# Matee Wiki - iOS - Release - Screenshots

- When creating production-ready screenshots (AppStore, landing pages, etc) it's a nice detail to do it the "Apple way"
- That means 9:41 time, full signal, full wifi and full battery .. [curious why?](https://www.engadget.com/2014-04-14-why-9-41-am-is-the-always-the-time-displayed-on-iphones-and-ipad.html)

## xcrun simctl
- Since Xcode 11 it's possible to modify these values directly in the Simulator via `xcrun simctl` - find more [here](https://apple.stackexchange.com/q/154511)
- However this feature [has stoped working](https://stackoverflow.com/q/74507031) in Xcode 14.1 and is still broken (Xcode 15.2 at the time of writing this)

## SimulatorStatusMagic
- Download [SimulatorStatusMagic](https://github.com/shinydevelopment/SimulatorStatusMagic) and run `build_and_inject.sh booted` - look into docs for more info
- If you need to modify some values you have to change it in `SDStatusBarManager/SDStatusBarOverriderPost[iOS-version].m`
- For example if you don't want to show battery percentage change `ProminentlyShowBatteryDetailStatusBarItem` to `NO`

## Photoshop
- Of course you can always just Photoshop the values, this is easy when the background is a simple color, it gets complicated for gradients/photos/etc
- You can find default status bar in the [Apple Design Resources](https://developer.apple.com/design/resources/)
- Two simple templates for iPhone 15 screenshots (1179x2556) are available here: [screenshot](img/screenshots/iphone15.psd) / [mockup](img/screenshots/iphone15-device.psd)
