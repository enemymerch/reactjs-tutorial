# Çocuk Bileşenleri Yönetme

Bu başlıkla oluşturduğumuz TaskBoard bileşene, içerisindeki çocuk bileşenler olan Task bileşenlerini silmek ve güncelleştirmek için ihtiyacımız olan iki tane fonksiyon ekleyeceğiz. Ekleyeceğimiz fonksiyonlar daha önceden oluşturduğumuz **tasks **adlı state'in durumunu gerektiği şekilde güncelleştirecekler.

_**bileseniSil**_ fonksiyonu

```js
         bileseniSil: function (index) {
            var taskArr = this.state.tasks;
            taskArr.splice(index,1);
            this.setState({
                tasks: taskArr
            });
        }
```

Üst kısımdaki kodda gördüğümüz gibi _**bileseniSil**_ fonksiyonu, _**index**_** **adında bir parametre alıyor. Bu aldığı parametre de Task bileşenin index'i. TaskBoard bileşeninde'in state'i olarak tuttuğumuz **tasks** değişkeninin içerisinden gereken index'deki değişkeni siliyoruz. Ve sonuç olarak bir Task bileşeni silinmiş oluyor.

_**bileseniGüncelle**_ fonksiyonu

```
        bileseniGüncelle: function (yeniText, index) {
            var taskArr = this.state.tasks;
            taskArr[index] = yeniText;
            this.setState({
                tasks: taskArr
            });
        }
```



