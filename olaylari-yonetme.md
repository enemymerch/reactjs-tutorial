# Olayları Yönetme

Bu başlıkta ReactJS de olayları yönetmekten bahsediyor olacağız. Projeye ayrı olarak css dosyası eklendim. Dosyayı [buradan ](https://drive.google.com/drive/folders/0BxLeFDQhe16BdG4wcFpySU51UHc?usp=sharing)indirip projenize ekleyebilirsiniz.

İlk önce Task adında bir bileşen oluşturacağız ve bu bileşenin iki tane button'ı olucak.

```js
    var Task = React.createClass({
        render: function () {
            return (
                    <div className="commentContainer">
                        <div>Bu bizim görevimiz!</div>
                        <button className="button-primary">Edit</button>
                        <button className="button-danger">Remove</button>
                    </div>
            );
        }
    });
```


