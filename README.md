## Requirements

- iOS 7+
- Xcode 8+

## Installation

ZFPlayer is available through [CocoaPods](https://cocoapods.org). To install it,use player template simply add the following line to your Podfile:

```objc
pod 'ZFPlayer', '~> 3.0'
```

Use default controlView simply add the following line to your Podfile:

```objc
pod 'ZFPlayer/ControlView', '~> 3.0'
```
Use AVPlayer simply add the following line to your Podfile:

```objc
pod 'ZFPlayer/AVPlayer', '~> 3.0'
```
如果使用AVPlayer边下边播可以参考使用[KTVHTTPCache](https://github.com/ChangbaDevs/KTVHTTPCache)

Use ijkplayer simply add the following line to your Podfile:

```objc
pod 'ZFPlayer/ijkplayer', '~> 3.0'
```
[IJKMediaFramework SDK](https://gitee.com/renzifeng/IJKMediaFramework) support cocoapods

Use KSYMediaPlayer simply add the following line to your Podfile:

```objc
pod 'ZFPlayer/KSYMediaPlayer', '~> 3.0'
```
[KSYMediaPlayer SDK](https://github.com/ksvc/KSYMediaPlayer_iOS) support cocoapods

## Usage introduce

####  ZFPlayerController
Main classes, two initialization methods, normal mode initialization and list style initialization (tableView, collection)

Normal style initialization 

```objc
ZFPlayerController *player = [ZFPlayerController playerWithPlayerManager:playerManager containerView:containerView];
ZFPlayerController *player = [[ZFPlayerController alloc] initwithPlayerManager:playerManager containerView:containerView];
```

List style initialization

```objc
ZFPlayerController *player = [ZFPlayerController playerWithScrollView:tableView playerManager:playerManager containerViewTag:containerViewTag];
ZFPlayerController *player = [ZFPlayerController alloc] initWithScrollView:tableView playerManager:playerManager containerViewTag:containerViewTag];
```

#### ZFPlayerMediaPlayback
For the playerMnager,you must conform `ZFPlayerMediaPlayback` protocol,custom playermanager can supports any player SDK，such as `AVPlayer`,`MPMoviePlayerController`,`ijkplayer`,`vlc`,`PLPlayerKit`,`KSYMediaPlayer`and so on，you can reference the `ZFAVPlayerManager`class.

```objc
Class<ZFPlayerMediaPlayback> *playerManager = ...;
```

#### ZFPlayerMediaControl
This class is used to display the control layer, and you must conform the ZFPlayerMediaControl protocol, you can reference the `ZFPlayerControlView` class.

```objc
UIView<ZFPlayerMediaControl> *controlView = ...;
player.controlView = controlView;
```

## Usage

#### Normal Style

```objc
/// Your custom playerManager must conform `ZFPlayerMediaPlayback` protocol.
Class<ZFPlayerMediaPlayback> *playerManager = ...;

/// playerController
ZFPlayerController *player = [ZFPlayerController playerWithPlayerManager:playerManager containerView:self.containerView];
player.controlView = controlView<ZFPlayerMediaControl>;
playerManager.assetURL = [NSURL URLWithString:...];
```

#### List style

```objc
/// Your custom playerManager must conform `ZFPlayerMediaPlayback` protocol.
Class<ZFPlayerMediaPlayback> *playerManager = ...;

/// playerController
ZFPlayerController *player = [ZFPlayerController playerWithScrollView:tableView playerManager:playerManager containerViewTag:tag<NSInteger>];
player.controlView = controlView<ZFPlayerMediaControl>;
self.player.assetURLs = array<NSURL *>;
```

Rotate the video the viewController must implement

```objc
- (BOOL)shouldAutorotate {
    return player.shouldAutorotate;
}
```




