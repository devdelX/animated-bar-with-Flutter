# animated-bar-with-Flutter
This is my sample code,

class SearchPage extends StatefulWidget{

  final PageController tab;
  SearchPage({Key key, this.tab}) : super(key: key);

  @override
  State<StatefulWidget> createState() {
    return _SearchPageState();
  }

}

class _SearchPageState extends State<SearchPage> {

  @override
  void initState() {
    super.initState();
  }

  @override
  void dispose() {
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Material(
      color: Colors.transparent,
        child: Stack(
          children: [
            Container(
              height: MediaQuery.of(context).size.height,
              //color: Colors.black,
            ),
            ClipPath(
              clipper: HeaderCurse(),
              child: Container(
                padding: EdgeInsets.only(left: 20, right: 20, top: 90),
                width: MediaQuery.of(context).size.width,
                height: 250,
                decoration: BoxDecoration(
                  gradient: AppColors.primaryGradient,
                ),
              ),
            ),
          ],
        ),
    );
  }

}

class HeaderCurse extends CustomClipper<Path> {

  @override
  Path getClip(Size size) {
    var path = Path();
    path.lineTo(0.0, size.height - 75);

    var controlPoint1 = Offset(75, size.height - 95);
    var controlPoint2 = Offset(size.width * 0.2, size.height + 55);
    var endPoint = Offset(size.width * 0.5, size.height - 25);

    path.cubicTo(controlPoint1.dx, controlPoint1.dy, controlPoint2.dx,
        controlPoint2.dy, endPoint.dx, endPoint.dy);

    // path.lineTo(175, size.height);
    //
    var sc1 = Offset(size.width * 0.7, size.height - 75);
    var sc2 = Offset(size.width * 0.7, size.height + 25);
    var scEp = Offset(size.width * 0.87, size.height - 50);

    path.cubicTo(sc1.dx, sc1.dy, sc2.dx,
        sc2.dy, scEp.dx, scEp.dy);

    var firstControlPoint = new Offset(size.width * 0.95, size.height - 80);
    var firstEndPoint = new Offset(size.width, size.height - 75);
    path.quadraticBezierTo(firstControlPoint.dx, firstControlPoint.dy, firstEndPoint.dx, firstEndPoint.dy);

    path.lineTo(size.width, 0);
    path.close();
    return path;
  }

  @override
  bool shouldReclip(CustomClipper<Path> oldClipper) => false;

}
