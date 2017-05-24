# Çocuk Bileşenleri Yönetme

Bu başlıkla oluşturduğumuz TaskBoard bileşene, içerisindeki çocuk bileşenler olan Task bileşenlerini silmek ve güncelleştirmek için ihtiyacımız olan iki tane fonksiyon ekleyeceğiz. Ekleyeceğimiz fonksiyonlar daha önceden oluşturduğumuz **tasks **adlı state'in durumunu gerektiği şekilde güncelleştirecekler.

_**bileseniSil**_ fonksiyonu

```
         bileseniSil: function (index) {
            var taskArr = this.state.tasks;
            taskArr.splice(index,1);
            this.setState({
                tasks: taskArr
            });
        }
```



