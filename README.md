# instagram-clone2
import 'package:flutter/material.dart';

void main() => runApp(const MyApp());

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      debugShowCheckedModeBanner: false,
      //home: MyHomePage(),
      initialRoute: '/',
      routes: {
        '/': (context) => MyHomePage(),
        '/forgetPassword': (context) => forgetPassword(),
        '/emailSingUp': (context) => emailSingUp(),
        '/realHomePage': (context) => realHomePage()
      },
    );
  }
}

class MyHomePage extends StatelessWidget {
  TextEditingController t1 = TextEditingController();
  TextEditingController t2 = TextEditingController();
  MyHomePage({Key? key}) : super(key: key);
  final String name = 'Instagram';
  @override
  Widget build(BuildContext context) {
    kayitOl() {
      final String eposta = 'mensar@gmail.com';
      final String sifre = '123456';
      if (t1.text == eposta && t2.text == sifre) {
        Navigator.pushNamed(context, '/realHomePage');
      }
    }

    return SafeArea(
      child: Scaffold(
        backgroundColor: Colors.white,
        bottomNavigationBar: BottomAppBar(
          child: Row(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              Text('Hesabın yok mu'),
              TextButton(
                  onPressed: () {
                    Navigator.pushNamed(context, '/emailSingUp');
                  },
                  child: Text(
                    "Kaydol",
                    style: TextStyle(color: Colors.blue),
                  ))
            ],
          ),
          color: Colors.grey[300],
        ),
        body: Center(
          child: Column(
            children: [
              Padding(padding: EdgeInsets.all(30)),
              Image.network(
                'https://upload.wikimedia.org/wikipedia/commons/thumb/2/2a/Instagram_logo.svg/2560px-Instagram_logo.svg.png',
                height: MediaQuery.of(context).size.height * 0.1,
                width: MediaQuery.of(context).size.width * 0.70,
              ),
              Padding(padding: EdgeInsets.all(25)),
              Container(
                width: MediaQuery.of(context).size.width * 0.83,
                height: 36,
                child: TextField(
                  controller: t1,
                  maxLines: 1,
                  style: TextStyle(
                    fontSize: 17,
                  ),
                  textAlignVertical: TextAlignVertical.center,
                  decoration: InputDecoration(
                    filled: true,
                    border: OutlineInputBorder(
                        borderSide: BorderSide.none,
                        borderRadius: BorderRadius.all(Radius.circular(5))),
                    fillColor: Colors.grey[350],
                    contentPadding: EdgeInsets.fromLTRB(20, 0, 20, 0),
                    hintText: 'Telefon numarası kullanıcı adı yada e-posta',
                  ),
                ),
              ),
              Padding(padding: EdgeInsets.all(5)),
              SizedBox(
                width: MediaQuery.of(context).size.width * 0.83,
                height: 36,
                child: TextField(
                  controller: t2,
                  maxLines: 1,
                  style: TextStyle(
                    fontSize: 17,
                  ),
                  textAlignVertical: TextAlignVertical.center,
                  decoration: InputDecoration(
                    filled: true,
                    border: OutlineInputBorder(
                        borderSide: BorderSide.none,
                        borderRadius: BorderRadius.all(Radius.circular(5))),
                    fillColor: Colors.grey[350],
                    contentPadding: EdgeInsets.fromLTRB(20, 0, 20, 0),
                    hintText: 'Şifre',
                  ),
                ),
              ),
              Padding(padding: EdgeInsets.all(10)),
              Container(
                width: MediaQuery.of(context).size.width * 0.83,
                child: ElevatedButton(
                  onPressed: () {
                    kayitOl();
                  },
                  child: Text('Giriş Yap'),
                  style: ButtonStyle(
                    backgroundColor:
                        MaterialStateProperty.all(Colors.blue[400]),
                  ),
                ),
              ),
              Padding(padding: EdgeInsets.all(15)),
              Text(
                '------- YA DA -------',
                style: TextStyle(
                  color: Colors.grey,
                  fontSize: MediaQuery.of(context).size.width * 0.035,
                ),
              ),
              Padding(padding: EdgeInsets.all(20)),
              Row(
                mainAxisAlignment: MainAxisAlignment.center,
                children: [
                  Image.network(
                      "https://upload.wikimedia.org/wikipedia/commons/thumb/f/fb/Facebook_icon_2013.svg/1024px-Facebook_icon_2013.svg.png",
                      width: 25,
                      height: 25),
                  TextButton(
                    onPressed: () {},
                    child: Text(
                      'Facebook ile giriş yap',
                      style: TextStyle(color: Colors.blue),
                    ),
                  )
                ],
              ),
              Padding(padding: EdgeInsets.all(20)),
              TextButton(
                  onPressed: () {
                    Navigator.pushNamed(context, '/forgetPassword');
                  },
                  child: Text(
                    'Şifreni mi unuttun?',
                    style: TextStyle(color: Colors.indigo[800]),
                  )),
            ],
          ),
        ),
      ),
    );
  }
}

class forgetPassword extends StatelessWidget {
  const forgetPassword({Key? key}) : super(key: key);

  final String fMessage = 'Giriş Yaparken Sorun mu Yaşıyorsun?';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      bottomNavigationBar: Container(
        color: Colors.grey[350],
        height: MediaQuery.of(context).size.height * 0.05,
        child: Row(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            TextButton(
                onPressed: () {
                  Navigator.pop(context);
                },
                child: Text('Giriş Ekranına Dön'))
          ],
        ),
      ),
      body: SafeArea(
        child: Center(
          child: Column(children: [
            Padding(padding: EdgeInsets.all(25)),
            Icon(
              Icons.lock,
              size: 60,
            ),
            Padding(padding: EdgeInsets.all(5)),
            Text(
              fMessage,
              style: TextStyle(
                  color: Colors.black,
                  fontSize: 15,
                  fontWeight: FontWeight.w200),
            ),
            Padding(padding: EdgeInsets.all(5)),
            Text(
              'E-posta adresini, telefon numaranı veya kullanıcı',
              style: TextStyle(color: Colors.grey),
            ),
            Text(
              'adını gir ve hesabına yeniden girebilmen için',
              style: TextStyle(color: Colors.grey),
            ),
            Text(
              'sana bir bağlantı gönderelim',
              style: TextStyle(color: Colors.grey),
            ),
            Padding(padding: EdgeInsets.all(10)),
            Container(
              width: MediaQuery.of(context).size.width * 0.83,
              height: 36,
              child: TextField(
                maxLines: 1,
                style: TextStyle(
                  fontSize: 17,
                ),
                textAlignVertical: TextAlignVertical.center,
                decoration: InputDecoration(
                  filled: true,
                  border: OutlineInputBorder(
                      borderSide: BorderSide.none,
                      borderRadius: BorderRadius.all(Radius.circular(5))),
                  fillColor: Colors.grey[350],
                  contentPadding: EdgeInsets.fromLTRB(20, 0, 20, 0),
                  hintText: 'Telefon numarası kullanıcı adı yada e-posta',
                ),
              ),
            ),
            Padding(padding: EdgeInsets.all(10)),
            Container(
              width: MediaQuery.of(context).size.width * 0.83,
              child: ElevatedButton(
                onPressed: () {},
                child: Text('Giriş Bağlantısı Gönder'),
                style: ButtonStyle(
                  backgroundColor: MaterialStateProperty.all(Colors.blue[400]),
                ),
              ),
            ),
            Padding(padding: EdgeInsets.all(10)),
            Text(
              '------- YA DA -------',
              style: TextStyle(
                color: Colors.grey,
                fontSize: MediaQuery.of(context).size.width * 0.035,
              ),
            ),
            Padding(padding: EdgeInsets.all(5)),
            TextButton(
                onPressed: () {
                  Navigator.push(context,
                      MaterialPageRoute(builder: (context) => emailSingUp()));
                },
                child: Text(
                  'Yeni Hesap Oluştur',
                  style: TextStyle(color: Colors.black),
                ))
          ]),
        ),
      ),
    );
  }
}

class emailSingUp extends StatelessWidget {
  const emailSingUp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.white,
      bottomNavigationBar: Container(
        color: Colors.grey[350],
        height: MediaQuery.of(context).size.height * 0.09,
        child: Column(
          children: [
            TextButton(
                onPressed: () {
                  Navigator.pop(context);
                },
                child: Text('Önceki Ekrana Geri Dön')),
            Row(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Text('Hesabın var mı'),
                TextButton(
                    onPressed: () {
                      Navigator.pushNamed(context, '/');
                    },
                    child: Text(
                      "Giriş Yap",
                      style: TextStyle(color: Colors.blue),
                    ))
              ],
            )
          ],
        ),
      ),
      body: Center(
        child: Column(
          children: [
            Padding(padding: EdgeInsets.all(10)),
            Image.network(
              'https://upload.wikimedia.org/wikipedia/commons/thumb/2/2a/Instagram_logo.svg/2560px-Instagram_logo.svg.png',
              height: MediaQuery.of(context).size.height * 0.1,
              width: MediaQuery.of(context).size.width * 0.70,
            ),
            Padding(padding: EdgeInsets.all(10)),
            Text('Arkadaşlarının fotoğraf ve',
                style: TextStyle(color: Colors.grey[400])),
            Text('videolarını görmek için kaydol.',
                style: TextStyle(color: Colors.grey[400])),
            Padding(padding: EdgeInsets.all(10)),
            Container(
              width: MediaQuery.of(context).size.width * 0.83,
              child: ElevatedButton(
                onPressed: () {},
                child: Row(
                  mainAxisAlignment: MainAxisAlignment.center,
                  children: [
                    Padding(
                      padding: const EdgeInsets.fromLTRB(0, 0, 5, 0),
                      child: Container(
                        color: Colors.white,
                        width: 20,
                        height: 20,
                        child: Padding(
                          padding: EdgeInsets.fromLTRB(10, 3, 0, 0),
                          child: Text(
                            'f',
                            style: TextStyle(
                                color: Colors.blue[700],
                                fontSize: 20,
                                fontWeight: FontWeight.bold),
                          ),
                        ),
                      ),
                    ),
                    Text('Giriş Bağlantısı Gönder'),
                  ],
                ),
                style: ButtonStyle(
                  backgroundColor: MaterialStateProperty.all(Colors.blue[700]),
                ),
              ),
            ),
            Padding(padding: EdgeInsets.all(10)),
            Text(
              '------- YA DA -------',
              style: TextStyle(
                color: Colors.grey,
                fontSize: MediaQuery.of(context).size.width * 0.035,
              ),
            ),
            Padding(padding: EdgeInsets.all(5)),
            Container(
              width: MediaQuery.of(context).size.width * 0.83,
              height: 36,
              child: TextField(
                maxLines: 1,
                style: TextStyle(
                  fontSize: 17,
                ),
                textAlignVertical: TextAlignVertical.center,
                decoration: InputDecoration(
                  filled: true,
                  border: OutlineInputBorder(
                      borderSide: BorderSide.none,
                      borderRadius: BorderRadius.all(Radius.circular(5))),
                  fillColor: Colors.grey[350],
                  contentPadding: EdgeInsets.fromLTRB(20, 0, 20, 0),
                  hintText: 'Cep Telefonu Numarası veya E-posta',
                ),
              ),
            ),
            Padding(padding: EdgeInsets.all(5)),
            Container(
              width: MediaQuery.of(context).size.width * 0.83,
              height: 36,
              child: TextField(
                maxLines: 1,
                style: TextStyle(
                  fontSize: 17,
                ),
                textAlignVertical: TextAlignVertical.center,
                decoration: InputDecoration(
                  filled: true,
                  border: OutlineInputBorder(
                      borderSide: BorderSide.none,
                      borderRadius: BorderRadius.all(Radius.circular(5))),
                  fillColor: Colors.grey[350],
                  contentPadding: EdgeInsets.fromLTRB(20, 0, 20, 0),
                  hintText: 'Adı Soyadı',
                ),
              ),
            ),
            Padding(padding: EdgeInsets.all(5)),
            Container(
              width: MediaQuery.of(context).size.width * 0.83,
              height: 36,
              child: TextField(
                maxLines: 1,
                style: TextStyle(
                  fontSize: 17,
                ),
                textAlignVertical: TextAlignVertical.center,
                decoration: InputDecoration(
                  filled: true,
                  border: OutlineInputBorder(
                      borderSide: BorderSide.none,
                      borderRadius: BorderRadius.all(Radius.circular(5))),
                  fillColor: Colors.grey[350],
                  contentPadding: EdgeInsets.fromLTRB(20, 0, 20, 0),
                  hintText: 'Kullanıcı Adı',
                ),
              ),
            ),
            Padding(padding: EdgeInsets.all(5)),
            Container(
              width: MediaQuery.of(context).size.width * 0.83,
              height: 36,
              child: TextField(
                maxLines: 1,
                style: TextStyle(
                  fontSize: 17,
                ),
                textAlignVertical: TextAlignVertical.center,
                decoration: InputDecoration(
                  filled: true,
                  border: OutlineInputBorder(
                      borderSide: BorderSide.none,
                      borderRadius: BorderRadius.all(Radius.circular(5))),
                  fillColor: Colors.grey[350],
                  contentPadding: EdgeInsets.fromLTRB(20, 0, 20, 0),
                  hintText: 'Şifre',
                ),
              ),
            ),
            Padding(padding: EdgeInsets.all(10)),
            Container(
              width: MediaQuery.of(context).size.width * 0.83,
              child: ElevatedButton(
                onPressed: () {},
                child: Text('Kaydol'),
                style: ButtonStyle(
                  backgroundColor: MaterialStateProperty.all(Colors.blue[400]),
                ),
              ),
            ),
          ],
        ),
      ),
    );
  }
}

class realHomePage extends StatelessWidget {
  const realHomePage({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.white,
        automaticallyImplyLeading: false,
        title: Row(
          mainAxisAlignment: MainAxisAlignment.start,
          children: [
            Image.network(
              'https://upload.wikimedia.org/wikipedia/commons/thumb/2/2a/Instagram_logo.svg/2560px-Instagram_logo.svg.png',
              height: MediaQuery.of(context).size.height * 0.10,
              width: MediaQuery.of(context).size.width * 0.3,
            ),
          ],
        ),
        actions: [
          Row(
            mainAxisAlignment: MainAxisAlignment.end,
            children: [
              IconButton(
                  onPressed: () {},
                  icon: Icon(
                    Icons.add_box_outlined,
                    color: Colors.black,
                  )),
              IconButton(
                  onPressed: () {},
                  icon: Icon(
                    Icons.favorite_border_outlined,
                    color: Colors.black,
                  )),
              IconButton(
                  onPressed: () {
                    Navigator.pop(context);
                  },
                  icon: Icon(Icons.send, color: Colors.black))
            ],
          )
        ],
      ),
      body: realPage(),
    );
  }
}


class realPage extends StatefulWidget {
  const realPage({Key? key}) : super(key: key);

  @override
  _realPageState createState() => _realPageState();
}

class _realPageState extends State<realPage> {
  final List baslikListesi = <String>['aliyko', 'easymen', 'shutup', 'john93'];
  @override
  Widget build(BuildContext context) {
    return ListView(
      children: [
        Container(
          child: Column(
            children: [
              Container(
                margin: new EdgeInsets.symmetric(horizontal: 3.0),
                child: Row(
                  children: [
                    CircleAvatar(radius:18,
                      backgroundImage:
                          NetworkImage('https://cdn.wallpapersafari.com/60/16/8hFVK2.jpg'),
                      backgroundColor: Colors.pink,
                    ),
                    Padding(padding: EdgeInsets.all(3)),
                    Text(baslikListesi[0]),
                    Spacer(),
                    IconButton(onPressed: () {}, icon: Icon(Icons.more_vert)),Padding(padding:EdgeInsets.all(3)),
                  ],
                ),
              ),              Divider(
                color: Colors.grey,),Container(height: MediaQuery.of(context).size.width*1,constraints: BoxConstraints(maxHeight: 300),
                  child: Image.network('https://www.teahub.io/photos/full/3-36277_wallpapers-for-blue-flaming-skull-wallpaper-data-src.jpg',scale: 1,width: double.infinity, 
          fit: BoxFit.fitWidth,),
                ),Row(children: [IconButton(onPressed: (){}, icon: Icon(Icons.favorite_border_outlined)),IconButton(onPressed: (){}, icon: Icon(Icons.chat_bubble_outline)),IconButton(onPressed: (){}, icon: Icon(Icons.send)),Spacer(),IconButton(onPressed: (){}, icon: Icon(Icons.bookmark_add_outlined)),],)
            ],
          ),
        ),        Container(
          child: Column(
            children: [
              Container(
                margin: new EdgeInsets.symmetric(horizontal: 3.0),
                child: Row(
                  children: [
                    CircleAvatar(radius:18,
                      backgroundImage:
                          NetworkImage('https://cdn.wallpapersafari.com/60/16/8hFVK2.jpg'),
                      backgroundColor: Colors.pink,
                    ),
                    Padding(padding: EdgeInsets.all(3)),
                    Text(baslikListesi[0]),
                    Spacer(),
                    IconButton(onPressed: () {}, icon: Icon(Icons.more_vert)),Padding(padding:EdgeInsets.all(3)),
                  ],
                ),
              ),              Divider(
                color: Colors.grey,),Container(height: MediaQuery.of(context).size.width*1,constraints: BoxConstraints(maxHeight: 300),
                  child: Image.network('https://www.teahub.io/photos/full/3-36277_wallpapers-for-blue-flaming-skull-wallpaper-data-src.jpg',scale: 1,width: double.infinity, 
          fit: BoxFit.fitWidth,),
                ),Row(children: [IconButton(onPressed: (){}, icon: Icon(Icons.favorite_border_outlined)),IconButton(onPressed: (){}, icon: Icon(Icons.chat_bubble_outline)),IconButton(onPressed: (){}, icon: Icon(Icons.send)),Spacer(),IconButton(onPressed: (){}, icon: Icon(Icons.bookmark_add_outlined)),],)
            ],
          ),
        ),        Container(
          child: Column(
            children: [
              Container(
                margin: new EdgeInsets.symmetric(horizontal: 3.0),
                child: Row(
                  children: [
                    CircleAvatar(radius:18,
                      backgroundImage:
                          NetworkImage('https://cdn.wallpapersafari.com/60/16/8hFVK2.jpg'),
                      backgroundColor: Colors.pink,
                    ),
                    Padding(padding: EdgeInsets.all(3)),
                    Text(baslikListesi[0]),
                    Spacer(),
                    IconButton(onPressed: () {}, icon: Icon(Icons.more_vert)),Padding(padding:EdgeInsets.all(3)),
                  ],
                ),
              ),              Divider(
                color: Colors.grey,),Container(height: MediaQuery.of(context).size.width*1,constraints: BoxConstraints(maxHeight: 300),
                  child: Image.network('https://www.teahub.io/photos/full/3-36277_wallpapers-for-blue-flaming-skull-wallpaper-data-src.jpg',scale: 1,width: double.infinity, 
          fit: BoxFit.fitWidth,),
                ),Row(children: [IconButton(onPressed: (){}, icon: Icon(Icons.favorite_border_outlined)),IconButton(onPressed: (){}, icon: Icon(Icons.chat_bubble_outline)),IconButton(onPressed: (){}, icon: Icon(Icons.send)),Spacer(),IconButton(onPressed: (){}, icon: Icon(Icons.bookmark_add_outlined)),],)
            ],
          ),
        ),        Container(
          child: Column(
            children: [
              Container(
                margin: new EdgeInsets.symmetric(horizontal: 3.0),
                child: Row(
                  children: [
                    CircleAvatar(radius:18,
                      backgroundImage:
                          NetworkImage('https://cdn.wallpapersafari.com/60/16/8hFVK2.jpg'),
                      backgroundColor: Colors.pink,
                    ),
                    Padding(padding: EdgeInsets.all(3)),
                    Text(baslikListesi[0]),
                    Spacer(),
                    IconButton(onPressed: () {}, icon: Icon(Icons.more_vert)),Padding(padding:EdgeInsets.all(3)),
                  ],
                ),
              ),              Divider(
                color: Colors.grey,),Container(height: MediaQuery.of(context).size.width*1,constraints: BoxConstraints(maxHeight: 300),
                  child: Image.network('https://www.teahub.io/photos/full/3-36277_wallpapers-for-blue-flaming-skull-wallpaper-data-src.jpg',scale: 1,width: double.infinity, 
          fit: BoxFit.fitWidth,),
                ),Row(children: [IconButton(onPressed: (){}, icon: Icon(Icons.favorite_border_outlined)),IconButton(onPressed: (){}, icon: Icon(Icons.chat_bubble_outline)),IconButton(onPressed: (){}, icon: Icon(Icons.send)),Spacer(),IconButton(onPressed: (){}, icon: Icon(Icons.bookmark_add_outlined)),],)
            ],
          ),
        ),        Container(
          child: Column(
            children: [
              Container(
                margin: new EdgeInsets.symmetric(horizontal: 3.0),
                child: Row(
                  children: [
                    CircleAvatar(radius:18,
                      backgroundImage:
                          NetworkImage('https://cdn.wallpapersafari.com/60/16/8hFVK2.jpg'),
                      backgroundColor: Colors.pink,
                    ),
                    Padding(padding: EdgeInsets.all(3)),
                    Text(baslikListesi[0]),
                    Spacer(),
                    IconButton(onPressed: () {}, icon: Icon(Icons.more_vert)),Padding(padding:EdgeInsets.all(3)),
                  ],
                ),
              ),              Divider(
                color: Colors.grey,),Container(height: MediaQuery.of(context).size.width*1,constraints: BoxConstraints(maxHeight: 300),
                  child: Image.network('https://www.teahub.io/photos/full/3-36277_wallpapers-for-blue-flaming-skull-wallpaper-data-src.jpg',scale: 1,width: double.infinity, 
          fit: BoxFit.fitWidth,),
                ),Row(children: [IconButton(onPressed: (){}, icon: Icon(Icons.favorite_border_outlined)),IconButton(onPressed: (){}, icon: Icon(Icons.chat_bubble_outline)),IconButton(onPressed: (){}, icon: Icon(Icons.send)),Spacer(),IconButton(onPressed: (){}, icon: Icon(Icons.bookmark_add_outlined)),],)
            ],
          ),
        ),        Container(
          child: Column(
            children: [
              Container(
                margin: new EdgeInsets.symmetric(horizontal: 3.0),
                child: Row(
                  children: [
                    CircleAvatar(radius:18,
                      backgroundImage:
                          NetworkImage('https://cdn.wallpapersafari.com/60/16/8hFVK2.jpg'),
                      backgroundColor: Colors.pink,
                    ),
                    Padding(padding: EdgeInsets.all(3)),
                    Text(baslikListesi[0]),
                    Spacer(),
                    IconButton(onPressed: () {}, icon: Icon(Icons.more_vert)),Padding(padding:EdgeInsets.all(3)),
                  ],
                ),
              ),              Divider(
                color: Colors.grey,),Container(height: MediaQuery.of(context).size.width*1,constraints: BoxConstraints(maxHeight: 300),
                  child: Image.network('https://www.teahub.io/photos/full/3-36277_wallpapers-for-blue-flaming-skull-wallpaper-data-src.jpg',scale: 1,width: double.infinity, 
          fit: BoxFit.fitWidth,),
                ),Row(children: [IconButton(onPressed: (){}, icon: Icon(Icons.favorite_border_outlined)),IconButton(onPressed: (){}, icon: Icon(Icons.chat_bubble_outline)),IconButton(onPressed: (){}, icon: Icon(Icons.send)),Spacer(),IconButton(onPressed: (){}, icon: Icon(Icons.bookmark_add_outlined)),],)
            ],
          ),
        ),        Container(
          child: Column(
            children: [
              Container(
                margin: new EdgeInsets.symmetric(horizontal: 3.0),
                child: Row(
                  children: [
                    CircleAvatar(radius:18,
                      backgroundImage:
                          NetworkImage('https://cdn.wallpapersafari.com/60/16/8hFVK2.jpg'),
                      backgroundColor: Colors.pink,
                    ),
                    Padding(padding: EdgeInsets.all(3)),
                    Text(baslikListesi[0]),
                    Spacer(),
                    IconButton(onPressed: () {}, icon: Icon(Icons.more_vert)),Padding(padding:EdgeInsets.all(3)),
                  ],
                ),
              ),              Divider(
                color: Colors.grey,),Container(height: MediaQuery.of(context).size.width*1,constraints: BoxConstraints(maxHeight: 300),
                  child: Image.network('https://www.teahub.io/photos/full/3-36277_wallpapers-for-blue-flaming-skull-wallpaper-data-src.jpg',scale: 1,width: double.infinity, 
          fit: BoxFit.fitWidth,),
                ),Row(children: [IconButton(onPressed: (){}, icon: Icon(Icons.favorite_border_outlined)),IconButton(onPressed: (){}, icon: Icon(Icons.chat_bubble_outline)),IconButton(onPressed: (){}, icon: Icon(Icons.send)),Spacer(),IconButton(onPressed: (){}, icon: Icon(Icons.bookmark_add_outlined)),],)
            ],
          ),
        ),        Container(
          child: Column(
            children: [
              Container(
                margin: new EdgeInsets.symmetric(horizontal: 3.0),
                child: Row(
                  children: [
                    CircleAvatar(radius:18,
                      backgroundImage:
                          NetworkImage('https://cdn.wallpapersafari.com/60/16/8hFVK2.jpg'),
                      backgroundColor: Colors.pink,
                    ),
                    Padding(padding: EdgeInsets.all(3)),
                    Text(baslikListesi[0]),
                    Spacer(),
                    IconButton(onPressed: () {}, icon: Icon(Icons.more_vert)),Padding(padding:EdgeInsets.all(3)),
                  ],
                ),
              ),              Divider(
                color: Colors.grey,),Container(height: MediaQuery.of(context).size.width*1,constraints: BoxConstraints(maxHeight: 300),
                  child: Image.network('https://www.teahub.io/photos/full/3-36277_wallpapers-for-blue-flaming-skull-wallpaper-data-src.jpg',scale: 1,width: double.infinity, 
          fit: BoxFit.fitWidth,),
                ),Row(children: [IconButton(onPressed: (){}, icon: Icon(Icons.favorite_border_outlined)),IconButton(onPressed: (){}, icon: Icon(Icons.chat_bubble_outline)),IconButton(onPressed: (){}, icon: Icon(Icons.send)),Spacer(),IconButton(onPressed: (){}, icon: Icon(Icons.bookmark_add_outlined)),],)
            ],
          ),
        ),        Container(
          child: Column(
            children: [
              Container(
                margin: new EdgeInsets.symmetric(horizontal: 3.0),
                child: Row(
                  children: [
                    CircleAvatar(radius:18,
                      backgroundImage:
                          NetworkImage('https://cdn.wallpapersafari.com/60/16/8hFVK2.jpg'),
                      backgroundColor: Colors.red,
                    ),
                    Padding(padding: EdgeInsets.all(3)),
                    Text(baslikListesi[0]),
                    Spacer(),
                    IconButton(onPressed: () {}, icon: Icon(Icons.more_vert)),Padding(padding:EdgeInsets.all(3)),
                  ],
                ),
              ),              Divider(
                color: Colors.grey,),Container(height: MediaQuery.of(context).size.width*1,constraints: BoxConstraints(maxHeight: 300),
                  child: Image.network('https://www.teahub.io/photos/full/3-36277_wallpapers-for-blue-flaming-skull-wallpaper-data-src.jpg',scale: 1,width: double.infinity, 
          fit: BoxFit.fitWidth,),
                ),Row(children: [IconButton(onPressed: (){}, icon: Icon(Icons.favorite_border_outlined)),IconButton(onPressed: (){}, icon: Icon(Icons.chat_bubble_outline)),IconButton(onPressed: (){}, icon: Icon(Icons.send)),Spacer(),IconButton(onPressed: (){}, icon: Icon(Icons.bookmark_add_outlined)),],)
            ],
          ),
        ),        Container(
          child: Column(
            children: [
              Container(
                margin: new EdgeInsets.symmetric(horizontal: 3.0),
                child: Row(
                  children: [
                    CircleAvatar(radius:18,
                      backgroundImage:
                          NetworkImage('https://cdn.wallpapersafari.com/60/16/8hFVK2.jpg'),
                      backgroundColor: Colors.black,
                    ),
                    Padding(padding: EdgeInsets.all(3)),
                    Text(baslikListesi[1]),
                    Spacer(),
                    IconButton(onPressed: () {}, icon: Icon(Icons.more_vert)),Padding(padding:EdgeInsets.all(3)),
                  ],
                ),
              ),              Divider(
                color: Colors.grey,),Container(height: MediaQuery.of(context).size.width*1,constraints: BoxConstraints(maxHeight: 300),
                  child: Image.network('https://www.teahub.io/photos/full/3-36277_wallpapers-for-blue-flaming-skull-wallpaper-data-src.jpg',scale: 1,width: double.infinity, 
          fit: BoxFit.fitWidth,),
                ),Row(children: [IconButton(onPressed: (){}, icon: Icon(Icons.favorite_border_outlined)),IconButton(onPressed: (){}, icon: Icon(Icons.chat_bubble_outline)),IconButton(onPressed: (){}, icon: Icon(Icons.send)),Spacer(),IconButton(onPressed: (){}, icon: Icon(Icons.bookmark_add_outlined)),],)
            ],
          ),
        ),        Container(
          child: Column(
            children: [
              Container(
                margin: new EdgeInsets.symmetric(horizontal: 3.0),
                child: Row(
                  children: [
                    CircleAvatar(radius:18,
                      backgroundImage:
                          NetworkImage('https://cdn.wallpapersafari.com/60/16/8hFVK2.jpg'),
                      backgroundColor: Colors.orange,
                    ),
                    Padding(padding: EdgeInsets.all(3)),
                    Text(baslikListesi[2]),
                    Spacer(),
                    IconButton(onPressed: () {}, icon: Icon(Icons.more_vert)),Padding(padding:EdgeInsets.all(3)),
                  ],
                ),
              ),              Divider(
                color: Colors.grey,),Container(height: MediaQuery.of(context).size.width*1,constraints: BoxConstraints(maxHeight: 300),
                  child: Image.network('https://www.teahub.io/photos/full/3-36277_wallpapers-for-blue-flaming-skull-wallpaper-data-src.jpg',scale: 1,width: double.infinity, 
          fit: BoxFit.fitWidth,),
                ),Row(children: [IconButton(onPressed: (){}, icon: Icon(Icons.favorite_border_outlined)),IconButton(onPressed: (){}, icon: Icon(Icons.chat_bubble_outline)),IconButton(onPressed: (){}, icon: Icon(Icons.send)),Spacer(),IconButton(onPressed: (){}, icon: Icon(Icons.bookmark_add_outlined)),],)
            ],
          ),
        )
      ],
    );
  }
}
