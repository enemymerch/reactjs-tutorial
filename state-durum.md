# State\( Durum \)

Bu başlık altında bileşenlerin statelerinden bahsedeceğiz. Stateler bileşenlere verdiğimiz özelliklere benziyorlar ama aralarındaki fark şu ki; bileşene bir özellik verdiğimizde bu özellik o bileşenin hayatının sonuna kadar atanmış olur. ReactJS'in stateleriyle beraber bileşenlerimize istediğimiz zaman kolaylıkla ve hızlıca değiştirebileceğimiz özellikler atamış oluyoruz.

Bir tane checkbox bileşeni oluşturmayla işe başlayalım.

```js
       var CheckBox = React.createClass({
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
    );
```

Bileşenlerin statelerine, özelliklerine oluşatuğimız şekilde "this.state" ile ulaşıyoruz ve üstteki kodda "checked" isimli bir state'imiz var. Ama state'in bir ilk değeri yok ve bileşlerin ilk kez render edilmeden önce state'i bir variable atamamız gerekicek. Bunuda "getInitialState" fonksiyonu ile yapıyoruz.

```js
    var CheckBox = React.createClass({
        getInitialState: function () {
            return({
                checked: false
            });
        },
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
    });
    ReactDOM.render(<CheckBox/>, document.getElementById('container'));
```

"getInitialState" methodu ile isteğimiz kadar state'i atayabiliriz. Ama şu an ihtiyacımız olan sadece "checked" state'ini atamak.

