# Çocuk Bileşenleri Yönetme 3

Bu başlıkta yeni Task bileşenlerini dinamik olarak nasıl ekleyebileceğimizi öğreneceğiz.

Bundan dolayı TaskBoard bileşenimize yeni bir textarea ve buttun elementi eklememiz gerekiyor.

TaskBoard bileşeninin yeni render fonksiyonu:

```js
        render: function () {
            return (
                <div className="container">
                    <textarea  defaultValue="Yeni Task" ref="yeniTaskTextAlanı"></textarea>
                    <br/>
                    <button onClick={this.yeniTaskEkle} className="button-default">Add New Task</button>
                    <div className="board">
                        {
                            this.state.tasks.map(this.getTask)
                        }
                    </div>
                </div>
            );
        }
```

Üstte gördüğümüz gibi textarea elementine _**yeni TaskTextAlanı**_ adıyla bir referans verdik.

Şimdide Yeni bileşeni eklememizi sağlayacak fonksiyonumuzu yazmamız gerekiyor.

```js
        yeniTaskEkle: function () {
            var taskArr = this.state.tasks;
            taskArr.push(this.refs.yeniTaskTextAlanı.value);
            this.setState({
                tasks: taskArr
            });
        }
```

**yeniTaskEkle** fonksiyonu ile referans verdiğimiz textarea elementinin değerini alıyoruz. Ve yeni Task bileşenimizi oluşturuyoruz.



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
            this.props.delete(this.props.index);
        },
        save: function () {
            this.props.save(this.refs.yaziAlani.value, this.props.index);
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
        yeniTaskEkle: function () {
            var taskArr = this.state.tasks;
            taskArr.push(this.refs.yeniTaskTextAlanı.value);
            this.setState({
                tasks: taskArr
            });
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
            return (<Task index={i} save={this.bileseniGüncelle} delete={this.bileseniSil}>{taskText}</Task>);
        },
        render: function () {
            return (
                <div className="container">
                    <textarea  defaultValue="Yeni Task" ref="yeniTaskTextAlanı"></textarea>
                    <br/>
                    <button onClick={this.yeniTaskEkle} className="button-default">Add New Task</button>
                    <div className="board">
                        {
                            this.state.tasks.map(this.getTask)
                        }
                    </div>
                </div>
            );
        }
    });


    ReactDOM.render(<TaskBoard/>, document.getElementById("container"));
</script>
</body>
</html>
```

**Sonuç**

![](/assets/sonuç.png)

Projemiz için son adımları bir sonraki başlıkta göreceğiz.

