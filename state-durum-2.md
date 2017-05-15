# State\(Durum\) 2

Bu başlıkta, kodumuza Olayları Yönetme başlığında kaldığımız yerden, yani Task Management Projemize devam edeceğiz.

Kaldığımız yer;

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
        edit: function () {
            alert("Task'ı düzenle.");
        },
        remove: function () {
            alert("Task'ı sil.")
        },
        render: function () {
            return (
                    <div className="commentContainer">
                        <div className="commentText">{this.props.children}</div>
                        <button onClick={this.edit} className="button-primary">Edit</button>
                        <button onClick={this.remove} className="button-danger">Remove</button>
                    </div>
            );
        }
    });
    ReactDOM.render(<div className="board">
        <Task>Dinamik Textli Görevimiz!</Task>
    </div>, document.getElementById("container"));
</script>
</body>
</html>
```

Hatırladığımız üzere üst kısımdaki kodda "edit" ve "delete" butonlarına bastığımızda sayfada herhangi bir değişiklik olmuyor; sadece "alert\(\)" methodu çağrılıyordu. Bu başlıkta yapacağımız değişiklikler ile Task bileşenimizin içerisindeki text'i "edit" tuşuyla değiştirebileceğiz.

Bileşenimize bir state ekleyeceğiz ve bu state text'imizin edit ya da normal modda olup olmadığını gösterecek.

