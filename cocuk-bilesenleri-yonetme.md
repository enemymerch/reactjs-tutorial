# Çocuk Bileşenleri Yönetme

Bu başlıkla oluşturduğumuz TaskBoard bileşene, içerisindeki çocuk bileşenler olan Task bileşenlerini silmek ve güncelleştirmek için ihtiyacımız olan iki tane fonksiyon ekleyeceğiz. Ekleyeceğimiz fonksiyonlar daha önceden oluşturduğumuz **tasks **adlı state'in durumunu gerektiği şekilde güncelleştirecekler.

_**bileseniSil**_ fonksiyonu

```js
         bileseniSil: function (index) {
            var taskArr = this.state.tasks;
            taskArr.splice(index,1);
            this.setState({
                tasks: taskArr
            });
        }
```

Üst kısımdaki kodda gördüğümüz gibi _**bileseniSil**_ fonksiyonu, _**index**_** **adında bir parametre alıyor. Bu aldığı parametre de Task bileşenin index'i. TaskBoard bileşeninde'in state'i olarak tuttuğumuz **tasks** değişkeninin içerisinden gereken index'deki değişkeni siliyoruz. Ve sonuç olarak bir Task bileşeni silinmiş oluyor.

_**bileseniGüncelle**_ fonksiyonu

```js
        bileseniGüncelle: function (yeniText, index) {
            var taskArr = this.state.tasks;
            taskArr[index] = yeniText;
            this.setState({
                tasks: taskArr
            });
        }
```

Bu fonksiyonda ise, array'in belli bir index'indeki değişkeni silmek yerine, o değişkeni güncelliyoruz.



**index.html**

```html
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
        bileseniGüncelle: function (yeniText, index) {
            var taskArr = this.state.tasks;
            taskArr[index] = yeniText;
            this.setState({
                tasks: taskArr
            });
        },
        bileseniSil: function (index) {
            var taskArr = this.state.tasks;
            taskArr.splice(index,1);
            this.setState({
                tasks: taskArr
            });
        },
        getTask: function (taskText, i) {
            return (<Task index={i}>{taskText}</Task>);
        },
        render: function () {
            return (
                    <div className="board">
                        {
                            this.state.tasks.map(this.getTask)
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



