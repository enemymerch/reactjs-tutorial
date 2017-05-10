# Bileşenler

ReactJS'de oluşturduğumuz ve yönettiğimiz her öge aslında bir bileşen\(componenet\). Ve bu bileşenleri ReactJS ile istenilen şekilde kontrol edebiliyoruz. Bileşenleri parçalayıp küçük bileşenler oluşturabilir ve ya olan bileşenleri birleştirip daha büyük bileşenler oluşturabiliriz. Sonuç olarak ReactJS ile oluşturduğunuz web uygulaması değişik bileşenlerden oluşmaktadır.

### Bileşen oluşturmak

Bileşen oluşturmak için

```js
    <script type="text/babel">

        var Comp  = React.createClass({
            render: function () {
                return (<h1>Bu bir reactJS bilesenidir!</h1>);
            }
        });
        ReactDOM.render(<Comp />, document.getElementById("example"));
</script>
```

kod parçasını kullanacağız. Demoda kullandığımız "div" element'imiz aynı şekilde duruyor. Farklı olarak yaptığımız şey şu;

```js
var Comp
```

Comp adında bir değişken oluşturduk. Ama bu bileşeni    _React.createClass\(\) _method'u ile oluşturduk. _createClass\(\) _method'u parametre olarak bir HTML ana element'i alıyor. Ve bir bu HTML elementini _render _ fonksiyonunu kullanarak oluşturduk.

