# Basit Demo

Bu başlık altında ilk basit ReactJS kodumuzu yazacağız ve  ReactJS'in bizim için nasıl HTML kodu ürettiğini görmüş olacağız.

1. İlk olarak kullandığımız editörde bir HTML sayfası oluşturuyoruz.
2. Sonrasında ReactJS'i kullanabilmemiz için gerekli kodu HTML sayfasının "head" element'i altına ekliyoruz.
3. "body" elementinin altına bir "div" element'i oluşturuyoruz ve bu element'e "example" id'sini veriyoruz.
4. Son olarakta

```js
    <script type="text/babel">
        ReactDOM.render(<h1>Hello ReactJS</h1>, document.getElementById("example"));
    </script>
```

kod parçasını "body" element'inin altına yerleştiriyoruz. Script type'ın "text/babel" olması bizim JSX syntax'ı üzerinden javascript yazdığımızı söylüyor ve bu syntax'ta yazdığımız kod sonuç olarak normal javascript koduna dönüştürülüyor. Ama ReactJS'i JSX syntax'ı ile yazmak çok daha basit.

```js
ReactDOM.render(<h1>Hello ReactJS</h1>, document.getElementById("example"));
```

render method'u ile yaptımız işlem ise, "body" element'inin  altında oluşturduğumuz "example" id'li "div" elementine erişip, "div" elementinin altına

```html
<h1>Hello ReactJS</h1>
```

bir "h1" elementi eklemek.

**index.html**

```js
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8" />
    <title>Hello World</title>
    <script src="../js/react.min.js"></script>
    <script src="../js/react-dom.min.js"></script>
    <script src="../js/browser.min.js"></script>
</head>
<body>
    <div id="example"></div>
    <script type="text/babel">

        ReactDOM.render(<h1>Hello ReactJS</h1>, document.getElementById("example"));
</script>
</body>
</html>
```

**Sonuç sayfamız**

![](/assets/BasicDemo.png)

