# Bileşenler 2

Bu başlıkta birden fazla HTML elementini bir ReactJS bileşeninde nasıl kullanıcağımızı görüceğiz.

#### Birden çok HTML elementli ReactJS Bileşeni

Önceki sayfada gördüğümüz üzere 

```js
        var Comp  = React.createClass({
            render: function () {
                return (<h1>Bu bir reactJS bilesenidir!</h1>);
            }
        });
```

createClass\(\) method'una bir ana HTML elementi vermemiz gerekiyor. Yani kodu biraz değiştirirsek ve bu hale getirirsek;

```
        var Comp  = React.createClass({
            render: function () {
                return (<h1>Bu bir HTML elementidir!</h1>
                        <h3>Bu da bir HTML elementidir!</h3>);
            }
        });
```



