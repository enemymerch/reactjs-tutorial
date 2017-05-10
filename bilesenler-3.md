# Bileşenler 3

Bu başlıkta ReactJS bileşenlerinin özelliklerini  ve HTML elementlerinden farklılaştıkları noktaları göreceğiz.

Her ReactJS bileşeni bir sınıfın objesi olduğundan dolayı \(hatırlatma : her bileşen createClass\(\) method'u ile oluşturuluyor\), bu objelerin html elementlerinde olan özelliklerden farklı olarak değişik özellikler ekleyebiliyoruz. Buda bileşenleri istediğimiz şekilde özelleştirebildiğimiz anlamına geliyor. Örneğin arabalarla ilgili bir uygulama yapıyoruz ve farklı arabaları göstermemiz gerekiyor. ReactJS ile tek yapmamız gereken bir araba bileşeni oluşturmak ve istenilen şekilde kullanmak.

```js

        var Araba  = React.createClass({
            render: function () {
                return (<div>
                    <h1>Marka :{this.props.marka}</h1>
                    <h2>Model :{this.props.model}</h2>
                    </div>);
            }
        });
```



