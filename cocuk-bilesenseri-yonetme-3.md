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

Üstte gördüğümüz gibi textarea elementine "yeni TaskTextAlanı" adıyla bir referans verdik.

Şimdide Yeni bileşeni eklememizi sağlayacak fonksiyonumuzu yazmamız gerekiyor.

