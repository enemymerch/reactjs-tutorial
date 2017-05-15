# State\( Durum \)

Bu başlık altında bileşenlerin statelerinden bahsedeceğiz. Stateler bileşenlere verdiğimiz özelliklere benziyorlar ama aralarındaki fark şu ki; bileşene bir özellik verdiğimizde bu özellik o bileşenin hayatının sonuna kadar atanmış olur. ReactJS'in stateleriyle beraber bileşenlerimize istediğimiz zaman kolaylıkla ve hızlıca değiştirebileceğimiz özellikler atamış oluyoruz.

Bir tane checkbox bileşeni oluşturmayla işe başlayalım.

```js
        render: function () {
            var msg;
            if(this.state.checked){
                msg = 'tıklı'
            }else{
                msg = 'tıklı degil'
            }
            return(
                    <div>
                        <input type="checkbox"/>
                        <h3>{msg}</h3>
                    </div>
            );
        }
```

Bileşenlerin statelerine, özelliklerine oluşatuğimız şekilde "this.state" ile ulaşıyoruz.

