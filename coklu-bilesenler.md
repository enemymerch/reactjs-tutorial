# Çoklu Bileşenler

Kodumuzun son halinde, sayfamızda üç tane **Task** bileşeni bulunuyordu. Ve bunların _**delete**_ ve _**edit **\_butonları tam anlamıyla çalışmıyor. Bileşenlerimizin içerisindeki elementlere nasıl eriştiğimizi bir önceki başlıkta görmüştük ama şu anki ileride _**delete**\_ görevini yapabilmek için bizim sayfamızda kaç tane task bileşenimizin olduğu, bu bileşenlerin kimliklerini v.b. bilgileri elimizde tutmamız gerekiyor. Bundan dolayı elimizdeki task bileşenlerini içerisine gömebileceğimiz bir büyük bileşenimiz'in olması gerekiyor.

_**TaskBoard**_ adında yeni bir bileşen oluşturmamız gerekiyor.

```js
var TaskBoard = React.createClass({

    });
```

Şimdi bu bileşenimiz'in içerisine Task bileşenlerini koyacağız. Yapmamız gereken şey TaskBoard bileşeni'nin içerisine stringlerden oluşan bir dizi'yi yeni bir state olarak eklemek. Bu state değişkeninin adı da tasks olacak. Bu state'imizi önceki başlıklardan öğrendiğimiz üzere getInitialState fonksiyonunda oluşturacağız.

```js
    var TaskBoard = React.createClass({
        getInitialState: function () {
            return{
                tasks: [
                    'Task 1',
                    'Task 2',
                    'Task 3'
                ]
            }
        }
    });
```

Şimdi yapmamız gereken ise, _**TaskBoard**_ bileşenini kullanabilmemiz için, bu bileşenin render fonksiyonunu oluşturmak olacak.

TaskBoard bileşenin içerisinde Task bileşenlerini tutan bir dizimiz\("tasks"\) var. render fonksiyonunda yapmak istediğimiz de, bu dizideki bileşenleri return edebilmek.

Başlangıç olarak bileşenlerimizi bir \_**div **\_elementinin içerisinde toplamamız gerekiyor.

```js
    var TaskBoard = React.createClass({
        getInitialState: function () {
            return{
                tasks: [
                    'Task 1',
                    'Task 2',
                    'Task 3'
                ]
            }
        },
        render: function () {
            return (
                    <div className="board">

                    </div>
            );
        }
    });
```

Şimdi ise, _**tasks**_ dizisinden stringleri çekip div elementinin içerisine gönmek. Bunuda javascript'in map fonksiyonunu kullanarak yapacağız. Map fonksiyonu ile ayrıntılı bilgiyi  [buradan ](https://www.w3schools.com/jsref/jsref_map.asp)öğrenebilirsiniz. Ama basitçe anlatmak gerekirse bir for-each döngüsü gib i, dizinin her elemanı için map fonksiyonun içerisine parametre olarak verilen fonksiyonu çağırıyor.

```js
    var TaskBoard = React.createClass({
        getInitialState: function () {
            return{
                tasks: [
                    'Task 1',
                    'Task 2',
                    'Task 3'
                ]
            }
        },
        render: function () {
            return (
                    <div className="board">
                        {
                            this.state.tasks.map(function (taskText, i) {
                                return (<Task>{taskText}</Task>);
                            })
                        }
                    </div>
            );
        }
    });
```

Map fonksiyonun içerisine verdiğimiz fonksiyon : **getTask**

```js
        getTask: function (taskText, i) {
            return (<Task>{taskText}</Task>);
        }
```

**taskText **ve **i **adında iki tane parametre alıyor. taskText parametresi **tasks **dizisindeki değişken'e , **i** parametresi de her değişkenin index'îne denk geliyor.

Bundan sonra yapmamız gereken; ReactDOM.render fonksiyonun'un içerisine Task bileşeni yerine TaskBoard bileşenini vermek.

```js
 ReactDOM.render(<TaskBoard/>, document.getElementById("container"));
```

Sonuç

![](/assets/multiChild.png)

Şu ana kadar birden fazla bileşeni bir büyük bileşen içerisinde toplamayı başardık. Ama çocuk bileşenlerimizin \(Task bileşenleri\) hala kendilerine özgü birer kimlikleri yok. Bu sorunu da ReactJS'in _**key **_özelliği ile çözebiliyoruz. Key özelliğini map fonksiyonu ile oluşturduğumuz her task bileşenine vermemiz gerekiyor. Bunuda map fonksiyonunun içerisine parametre olarak verdiğimiz fonksiyonun içerisinde çözeceğiz.

```js
        getTask: function (taskText, i) {
            return (<Task key={i}>{taskText}</Task>);
        }
```

ReactJS'in key özelliğini kullanarak TaskBoard içerisindeki Task bileşenlerine kendi özel kimliklerini verdik.

**index.html**

```js
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8" />
    <title>Hello React</title>
    <link rel="stylesheet" type="text/css" href="../css/main.css">
    <script src="../js/react.min.js"></script>
    <script src="../js/react-dom.min.js"></script>
    <script src="../js/browser.min.js"></script>
</head>
<body>
<div id="container"></div>

<script type="text/babel">

    var Task = React.createClass({
        getInitialState: function () {
            return(
                {editing: false}
            );
        },
        edit: function () {
            this.setState({
                editing: true
            });
        },
        remove: function () {
            alert("Task'ı sil.")
        },
        save: function () {
            var yeniText = this.refs.yaziAlani.value;
            alert(yeniText)
            this.setState({
                editing: false
            })
        },
        normalMode: function () {
            return (
                    <div className="commentContainer">
                        <div className="commentText">{this.props.children}</div>
                        <button onClick={this.edit} className="button-primary">Edit</button>
                        <button onClick={this.remove} className="button-danger">Remove</button>
                    </div>
            );
        },
        editingMode: function () {
            return (
                    <div className="commentContainer">
                        <textarea ref="yaziAlani" defaultValue={this.props.children}></textarea>
                        <button onClick={this.save} className="button-secondary">Save</button>
                    </div>
            );
        },
        render: function () {
            if(this.state.editing){
                return this.editingMode();
            }else{
                return this.normalMode();
            }
        }
    });

    var TaskBoard = React.createClass({
        getInitialState: function () {
            return{
                tasks: [
                    'Task 1',
                    'Task 2',
                    'Task 3'
                ]
            }
        },
        render: function () {
            return (
                    <div className="board">
                        {
                            this.state.tasks.map(function (taskText, i) {
                                return (<Task key={i}>{taskText}</Task>);
                            })
                        }
                    </div>
            );
        }
    });

    ReactDOM.render(<TaskBoard/>, document.getElementById("container"));
</script>
</body>
</html>
```

İleriki başlıklarda edit ve delete işlemlerini gerçekleştireceğiz.

