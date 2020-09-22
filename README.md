import 'package:flutter/material.dart';

void main() {
runApp(
mainLayout(),
);
}

Widget mainLayout() {
return MaterialApp(
home: Container(
color: Colors.white,
child: Column(children: [
Container(
height: 80,
padding: EdgeInsets.symmetric(horizontal: 16),
child: menuBar(),
),
Container(
height: 188,
margin: EdgeInsets.symmetric(vertical: 24),
child: productBanners(),
),
Container(
height: 44,
alignment: Alignment.topLeft,
padding: EdgeInsets.only(left: 16),
child: catalogHeader(),
),
Expanded(
child: catalogGrid(),
)
]),
),
);
}

Widget menuBar() {
return Row(
mainAxisAlignment: MainAxisAlignment.spaceBetween,
children: [
icon('https://i.postimg.cc/fkftcxBZ/menu.png', 24.0),
icon('https://i.postimg.cc/6yB6tgVx/search.png', 24.0),
],
);
}

Widget icon(name, size, {padding = 8.0}) {
return Container(
width: size,
height: size,
margin: EdgeInsets.all(padding),
child: Image.network(name),
);
}

Widget productBanners() {
return ListView(
scrollDirection: Axis.horizontal,
children: [
product('https://i.postimg.cc/w7rgsS6s/Origami-Chair.png', Colors.cyan,'First\nChair'),
product('https://i.postimg.cc/pmnxQqTc/Adirondack-Chair.png',Colors.yellow,'Second\nChair'),
// product('chair3d2', Colors.red, "Origami\nChair"),
// product('chair3d', Colors.green, "Adirondak\nChair"),
],
);
}

Widget product(
String iconName,
Color backgroundColor,
String title,
) {
return Material(
child: Container(
width: 188,
height: 188,
margin: EdgeInsets.only(left: 24),
decoration: BoxDecoration(
borderRadius: BorderRadius.all(Radius.circular(32)),
color: backgroundColor,
),
child: Stack(
children: [
Positioned(
left: 20,
top: 20,
child: Text(
title,
style: TextStyle(
color: Colors.white,
fontSize: 24,
decoration: null,
decorationStyle: null,
),
),
),
Positioned(
bottom: 0,
right: 0,
child: icon(iconName, 140.0),
)
],
),
),
);
}

Widget catalogHeader() {
return Material(
child: Text(
'Browse Furniture',
style: TextStyle(color: Colors.black, fontSize: 32.0),
),
);
}

Widget catalogGrid() {
return SingleChildScrollView(
child: Container(
padding: EdgeInsets.symmetric(horizontal: 16),
child: Column(
children: <Widget>[
catalogFirstRow(),
catalogSecondRow(),
catalogThirdRow(),
],
),
),
);
}

Widget catalogFirstRow() {
return Row(
mainAxisAlignment: MainAxisAlignment.spaceBetween,
children: <Widget>[
category('https://i.postimg.cc/RJJvDxKj/Chairs.png', 'Chairs'),
category('https://i.postimg.cc/zbm5McDM/Sofa.png', 'Sofa'),
category('https://i.postimg.cc/YvstNS5t/Racks.png', 'Racks'),
],
);
}

Widget catalogSecondRow() {
return Row(
mainAxisAlignment: MainAxisAlignment.spaceBetween,
children: <Widget>[
category('https://i.postimg.cc/RJ4mCJHL/Carpet.png', 'Carpet'),
category('https://i.postimg.cc/G8kr1xHp/Chandelier.png', 'Chandelier'),
category('https://i.postimg.cc/c6SttD7X/Bed.png', 'Bed'),
],
);
}

Widget catalogThirdRow() {
return Row(
mainAxisAlignment: MainAxisAlignment.spaceBetween,
children: <Widget>[
category('https://i.postimg.cc/Jsn1BXdT/Workstation.png', 'Workstation'),
category('https://i.postimg.cc/kVRqTmCK/Book-Shelf.png', 'Book Shelf'),
category('https://i.postimg.cc/Fkp4YFb5/Bean-Bag.png', 'Bean Bag'),
],
);
}

Widget category(String iconName, String name) {
return Material(
child: Column(
children: <Widget>[
icon(iconName, 60.0),
Text(
name,
style: TextStyle(
color: Colors.black,
fontSize: 12,
),
),
],
),
);
}
