# Olayları Yönetme

Bu başlıkta ReactJS de olayları yönetmekten bahsediyor olacağız. Projeye ayrı olarak css dosyası eklendim. Dosyayı [buradan ](https://drive.google.com/drive/folders/0BxLeFDQhe16BdG4wcFpySU51UHc?usp=sharing)indirip projenize ekleyebilirsiniz.

İlk önce Task adında bir bileşen oluşturacağız ve bu bileşenin iki tane butonu olacak.

```js
    var Task = React.createClass({
        render: function () {
            return (
                    <div className="commentContainer">
                        <div>Bizim görevimiz!</div>
                        <button onclick="edit" className="button-primary">Edit</button>
                        <button onclick="remove" className="button-danger">Remove</button>
                    </div>
            );
        }
    });
```

Kodda gördüğümüz üzere bu iki buton tıklanıldığında "edit" ve "remove" adında iki fonksiyonu çağırıyor.

Bu iki fonksiyonuda kodumuza eklememiz gerekiyor.

