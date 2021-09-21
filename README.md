#Support machine Vector For Regression (SVR)-Sklearn-dart
-Implementation of sklearn svr model to Flutter

##Introduction
This library uses pre-trained models using sklearn-learn and svr-tojson for python.You have to build it and 
export it in the asset directory of your flutter application.

##Steps to follows

-You create your SVR model in python using sklearn package,once done you use svr-tojson package to create your
json file who will contains all your attributs of your model.
-You install this package by doing this:
'''yaml
dependencies:
    svr:0.0.1
'''
-You Export your json file(model) into the asset like this:
'''yaml
flutter:
  uses-material-design: true
  assets:
    - assets/file.json
'''
-Import the library in your application and load the model:
'''dart
import 'package:flutter/material.dart';
import 'package:svr/SVR.dart';
import 'dart:convert';

void main() => runApp(new MaterialApp(
home: new HomePage(),
debugShowCheckedModeBanner: false)
);

class HomePage extends StatefulWidget {
@override
_HomePageState createState() {
return new _HomePageState();
}
}

class _HomePageState extends State<HomePage> {
SVR svr;

_HomePageState() {
loadModel("assets/svrmodel.json").then((x) {
this.svr = SVR.fromMap(json.decode(x));
});
}

@override
Widget build(BuildContext context) {
return Scaffold(            
// add any widget with svr.predict() callback
);
}
'''
