# FAB Circular Menu 
[![Pub package](https://img.shields.io/pub/v/fab_circular_menu_plus.svg)](https://pub.dev/packages/fab_circular_menu_plus)
[![License](https://img.shields.io/github/license/CsabaConsulting/fab_circular_menu_plus)](https://github.com/CsabaConsulting/fab_circular_menu_plus/blob/master/LICENSE)
![Null safety](https://img.shields.io/badge/null%20safety-true-brightgreen)
![Platform](https://img.shields.io/badge/platform-web%20%7C%20android%20%7C%20ios-ff69b4)

A Flutter package to create a nice circular menu using a Floating Action Button.

Originally inspired by [Mayur Kshirsagar](https://dribbble.com/mayurksgr)'s great
[FAB Microinteraction](https://dribbble.com/shots/4354100-Daily-UI-Challenge-Day-75-FAB-Microinteraction) design.
It is implemented as a [Flutter plugin by Mariano Cordova](https://pub.dev/packages/fab_circular_menu)
([source code](https://github.com/marianocordoba/fab-circular-menu/)). This plugin is the continuation
of the discontinued original plugin. I merged some of my bug fixes and made some changes to my liking.

I forked this plugin out of necessity and I have only a very limited time for maintenance, so PRs
are highly welcome if any change is desired.

![Showcase](https://i.imgur.com/ErrNnAw.gif)

## Installation

Just add `fab_circular_menu_plus` to your [pubspec.yml](https://flutter.io/using-packages/) file

```yml
dependencies:
  fab_circular_menu_plus: ^0.0.1
```

## Example

```dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Placeholder(),
        floatingActionButton: FabCircularMenuPlus(
          children: <Widget>[
            IconButton(icon: Icon(Icons.home), onPressed: () {
              print('Home');
            }),
            IconButton(icon: Icon(Icons.favorite), onPressed: () {
              print('Favorite');
            })
          ]
        )
      )
    );
  }
}
```

You can check for a more complete example in the [example](https://github.com/marianocordoba/fab-circular-menu/tree/master/example) directory.

## Customize

You can customize the widget appearance using the following properties:

| Property                | Description                                                                                                | Default                                                                                                      |
|-------------------------|------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| alignment               | Sets the widget alignment                                                                                  | `Alignment.bottomRight`                                                                                      |
| ringColor               | Sets the ring color                                                                                        | `accentColor`                                                                                                |
| ringDiameterLimitFactor | Sets the ring diameter limit factor                                                                        | `1.5`                                                                                                        |
| ringDiameter            | Sets the ring diameter                                                                                     | `screenWidth * ringDiameterLimitFactor` (portrait) <br> `screenHeight * ringDiameterLimitFactor` (landscape) |
| ringWidthLimitFactor    | Sets the ring width limit factor                                                                           | `0.2`                                                                                                        |
| ringWidth               | Sets the ring width                                                                                        | `ringDiameter * ringWidthLimitFactor`                                                                        |
| fabSize                 | Sets the FAB size                                                                                          | `64.0`                                                                                                       |
| fabElevation            | Sets the elevation for the FAB                                                                             | `8.0`                                                                                                        |
| fabColor                | Sets the FAB color                                                                                         | `primaryColor`                                                                                               |
| fabOpenColor            | Sets the FAB color while the menu is open. This property takes precedence over `fabColor`                  | -                                                                                                            |
| fabCloseColor           | Sets the FAB color while the menu is closed. This property takes precedence over `fabColor`                | -                                                                                                            |
| fabChild                | Sets the child inside the FAB. This property takes precedence over `fabOpenicon` and `fabCloseIcon`        | -                                                                                                            |
| fabOpenIcon             | Sets the FAB icon while the menu is open                                                                   | `Icon(Icons.menu)`                                                                                           |
| fabCloseIcon            | Sets the FAB icon while the menu is closed                                                                 | `Icon(Icons.close)`                                                                                          |
| fabMargin               | Sets the widget margin                                                                                     | `EdgeInsets.all(16.0)`                                                                                       |
| animationDuration       | Changes the animation duration                                                                             | `Duration(milliseconds: 800)`                                                                                |
| animationCurve          | Allows you to modify the animation curve                                                                   | `Curves.easeInOutCirc`                                                                                       |
| onDisplayChange         | This callback is called every time the menu is opened or closed, passing the current state as a parameter. | -                                                                                                            |

## Handling the menu programmatically

It is possible to handle the menu programmatically by using a [key](https://api.flutter.dev/flutter/foundation/Key-class.html).
Just create a key and set it in the `key` property of the `FabCircularMenuPlus`, then use the key to get the current state and open, close or check the status of the menu.

```dart
class MyApp extends StatelessWidget {
  final GlobalKey<FabCircularMenuPlusState> fabKey = GlobalKey();

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: RaisedButton(
          onPressed: () {
            if (fabKey.currentState.isOpen) {
              fabKey.currentState.close();
            } else {
              fabKey.currentState.open();
            }
          },
          child: Text('Toggle menu')
        ),
        floatingActionButton: FabCircularMenuPlus(
          key: fabKey,
          children: <Widget>[
            // ...
          ]
        )
      )
    );
  }
}
```

## Contributing

I will be very happy if you contribute to this project, feel free to submit a PR.
