# Çevreyi Kurmak

#### 1.Yöntem \(npm ve Web Strom\)

* [npm.com](https://www.gitbook.com/book/enemymerch/test/edit#)'dan Node.js ile beraber npm'i yükle.

* Kullanılan işletim sistemi fark etmeksizin komut satırına

```bash
npm install -g create-react-app // reactJS project creater

create-react-app my-app        // creating a project named "my-app"
cd my-app/                     // moving to mya-app dir.
npm start                      // deploying the project to localhost
```

komutlarını  kullanarak projeyi oluşturup, localhost'a gönderebiliyoruz.

Bu yöntem ile direk olarak bir ReactJS projesi oluşturmuş oluyoruz.

Detaylı kurulum için [ github.com/facebookincubator/create-react-app](https://github.com/facebookincubator/create-react-app) adresine göz atabilirsiniz.



Gerekli olan ReactJS dosyalarını bilgisayarınıza [buradan](https://www.gitbook.com/book/enemymerch/reactjs-tutorial/edit#) indirdikten sonra npm ile oluşturduğunuz projeyi Web Strom ile açın. Projenin altındaki src klasörüne .js uzantılı dosyaları ekleyip HTML sayfanızda local olarak kullanabilirsiniz.

```html
<!-- reactJS'in kendi kütüphanesi -->
<script src="../js/react.min.js"></script>
```

```html
<!-- reactJS'in DOM kütüaphanesi -->
<script src="../js/react-dom.min.js"></script>
```

```html
<!-- JSX'i javascript'e çeviren eden babel kütüphanesi -->
<script src="../js/browser.min.js"></script>
```

#### 

#### 2.Yöntem\(Web Strom\)

Web Strom editörü ile direk olarak React projesi oluşturarak devam edebilirsiniz.



