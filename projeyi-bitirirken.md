# Projeyi Bitirirken

Bu son başlığımız ve bu başlıkta şu an'a kadar öğrendiklerimiz ile düzgün çalışan bir Task Yönetim sayfası hazırlayacağız.

İlk önce sayfamıza düzen ve biraz renk vermesi için [_Bootstrap_](http://getbootstrap.com/)'i kullanacağız. Bootstrap'i kendi sitesinden indirip kullanabilirsiniz. İsterseniz de bu [link'te](https://drive.google.com/drive/folders/0BxLeFDQhe16BcFdvNk5VcnZkckE?usp=sharing) kendi projem için kullandığım css, fonts ve js klasörlerine erişebilirsiniz.

Gerekli bootstrap ve js linklerini projemize ekleyelim.

```html
    <link href="../css/bootstrap.min.css" rel="stylesheet">
    <!-- Other Js links-->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
    <script src="../js/bootstrap.min.js"></script>
    <!-- ReactJS Links -->
    <script src="../js/react.min.js"></script>
    <script src="../js/react-dom.min.js"></script>
    <script src="../js/browser.min.js"></script>
```

Önceli başlıklarda kullandığımız \_main.css \_dosyasını artık kullanmayacağız.

Ayrıca görünüş'ü biraz daha özelleştirebilmek için küçük bir css kodu eklememiz gerekiyor sayfamıza

```html
    <style>
        body{
            background-color: #9acfea;
            font-family: "Comic Sans MS";
        }
        .Task{
            background-color: #9acfea;
            border-color: #1b6d85;
            border: medium;
            border-style: double;
            margin: 3%;
            padding: 3%;
        }
        .TaskBoard{
            background-color: #2ecc71;
            margin: 3%;
            padding: 3%;
        }
    </style>
```

Sonrasında sayfamızın **body** kısmını güncellememiz gerekiyor.

Yeni **Body **kısmı:

```
    <div class="container">

            <h1 class="text-center text-primary" >ReactJS Beginner Tutorial</h1>
            <h2 class="text-center text-primary"> Task Yönetim Sistemi</h2>

            <br/>
            <br/>

            <div style="margin-top: 10%" id="board" >

            </div>
    </div>
```

**board** id'li div elementi ReactJS bileşenlerinin render edileceği bölüm olacak.

#### Proje Yapısı

Önceki başlıklarda TaskBoard bileşenimizin içerisinde Task bileşenlerini tutan bir tane task listesi\(_this.state.tasks_\) vardı. Projemiz  başlıca üç farklı Task başlığı altında toplanacak. Bunlar **notStarted, inProcess **ve **finished**. Yani her başlık için ayrı task listesi tutacağız. Bundan dolayı TaskBoard bileşenimizin içerisindeki fonksiyonları güncellememiz gerekicek.

İlk önce **getInitialState** fonksiyonumuzu değiştireceğiz.

Yeni **getInitialState** fonksiyonu:

```js
        getInitialState: function () {
            return{
                notStarted: [
                    'Task 1',
                    'Task 2',
                    'Task 3'
                ],
                inProcess: [
                    'Task 1',
                    'Task 2',
                    'Task 3'
                ],
                finished: [
                    'Task 1',
                    'Task 2',
                    'Task 3'
                ]
            }
        }
```

Sonrasında her Task listesini ayrı ayrı render edebilmek için önceden kullandığımız **getTask** fonksiyonunu silip her list'e için yeni fonksiyon yazıcağız.

Yeni task fonksiyonları:

```js
        getTaskNotStarted: function (taskText, i) {
            return (<Task durum="notStarted" index={i} prev={this.bileseniGerilet} next={this.bileseniIlerlet} save={this.bileseniGüncelle} delete={this.bileseniSil}>{taskText}</Task>);
        },
        getTaskInProcess: function (taskText, i) {
            return (<Task durum="inProcess" index={i} prev={this.bileseniGerilet} next={this.bileseniIlerlet} save={this.bileseniGüncelle} delete={this.bileseniSil}>{taskText}</Task>);
        },
        getTaskFinished: function (taskText, i) {
            return (<Task durum="finished" index={i} prev={this.bileseniGerilet} next={this.bileseniIlerlet} save={this.bileseniGüncelle} delete={this.bileseniSil}>{taskText}</Task>);
        }
```

Gördüğümüz gibi yeni fonksiyonlarımızda fazladan üç tane daha props veriliyor Task bileşenlerine. **durum** props'ının nedeni Task bileşeninin hangi listede oldğunu takip etmek için.** prev** ve **next** props'ları ile iki yeni fonksiyon veriliyor child Task bileşenlere. Bu fonksiyonlar'ın amaçı ise listeler arası Task bileşenlerini taşımak.

**bileseniGerilet **fonksiyonu,

```js
        bileseniGerilet: function (index, durum) {
            if(durum == "notStarted"){
                alert("Daha gerileyemez");
                return;
            }

            var taskArr1;
            var text;
            var taskArr2;
            if(durum == "finished"){
                taskArr1 = this.state.finished;
                text = taskArr1[index];
                taskArr1.splice(index,1);
                this.setState({
                    finished: taskArr1
                });
                taskArr2 = this.state.inProcess;
                taskArr2.push(text);
                this.setState({
                    inProcess: taskArr2
                });
            }else if(durum == "inProcess"){
                taskArr1 = this.state.inProcess;
                text = taskArr1[index];
                taskArr1.splice(index,1);
                this.setState({
                    inProcess: taskArr1
                });
                taskArr2 = this.state.notStarted;
                taskArr2.push(text);
                this.setState({
                    notStarted: taskArr2
                });
            }
        }
```

Task bileşeninin durum'una göre bileşeni ilerletiyor.

**bileseniIlerlet** fonksiyonu da bileseniGerilet fonksiyonuna çok benzer.

```js
        bileseniIlerlet: function (index, durum) {
            if(durum == "finished"){
                alert("Daha ilerleyemez");
                return;
            }


            if(durum == "notStarted"){
                var taskArr1 = this.state.notStarted;
                var text = taskArr1[index];
                taskArr1.splice(index,1);
                this.setState({
                    notStarted: taskArr1
                });
                var taskArr2 = this.state.inProcess;
                taskArr2.push(text);
                this.setState({
                    inProcess: taskArr2
                });
            }else if(durum == "inProcess"){
                var taskArr1 = this.state.inProcess;
                var text = taskArr1[index];
                taskArr1.splice(index,1);
                this.setState({
                    inProcess: taskArr1
                });
                var taskArr2 = this.state.finished;
                taskArr2.push(text);
                this.setState({
                    finished: taskArr2
                });
            }
        }
```

TaskBoard bileşeninde geri kalan fonksiyonları'da yeni yönetim sistemimize göre güncellememiz gerekiyor.

Yeni **yeniTaskEkle **fonksiyonu:

```js
        yeniTaskEkle: function () {
            var taskArr = this.state.notStarted;
            taskArr.push(this.refs.yeniTaskTextAlanı.value);
            this.setState({
                notStarted: taskArr
            });
        }
```



