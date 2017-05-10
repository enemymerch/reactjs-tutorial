# Bileşenler

ReactJS'de oluşturduğumuz ve yönettiğimiz her öge aslında bir bileşen\(componenet\). Ve bu bileşenleri ReactJS ile istenilen şekilde kontrol edebiliyoruz. Bileşenleri parçalayıp küçük bileşenler oluşturabilir ve ya olan bileşenleri birleştirip daha büyük bileşenler oluşturabiliriz. Sonuç olarak ReactJS ile oluşturduğunuz web uygulaması değişik bileşenlerden oluşmaktadır.

### Bileşen oluşturmak

Bileşen oluşturmak için

```js
    <script type="text/babel">
        var Bacon  = React.createClass({
            render: function () {
                return (<h1>This is a Simple compenent!</h1>);
            }
        });
        ReactDOM.render(<Bacon/>, document.getElementById("example"));
    </script>
```

kod parçasını kullanacağız. Demoda kullandığımız "div" element'imiz aynı şekilde duruyor. Farklı olarak yaptığımız şey şu;

```js
var Bacon
```



