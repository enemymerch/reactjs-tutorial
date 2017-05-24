# Çoklu Bileşenler

Kodumuzun son halinde, sayfamızda üç tane **Task** bileşeni bulunuyordu. Ve bunların _**delete**_ ve _**edit **\_butonları tam anlamıyla çalışmıyor. Bileşenlerimizin içerisindeki elementlere nasıl eriştiğimizi bir önceki başlıkta görmüştük ama şu anki ileride _**delete**\_ görevini yapabilmek için bizim sayfamızda kaç tane task bileşenimizin olduğu, bu bileşenlerin kimliklerini v.b. bilgileri elimizde tutmamız gerekiyor. Bundan dolayı elimizdeki task bileşenlerini içerisine gömebileceğimiz bir büyük bileşenimiz'in olması gerekiyor.

_**TaskBoard**_ adında yeni bir bileşen oluşturmamız gerekiyor.

```js
var TaskBoard = React.createClass({

    });
```

Şimdi bu bileşenimiz'in içerisine Task bileşenlerini koyacağız. Yapmamız gereken şey TaskBoard bileşeni'nin içerisine stringlerden oluşan bir dizi'yi yeni bir state olarak eklemek. Bu state değişkeninin adı da tasks olacak. Bu state'imizi önceki başlıklardan öğrendiğimiz üzere getInitialState fonksiyonunda oluşturacağız.

```js
    var TaskBoard = React.createClass({
        getInitialState: function () {
            return{
                tasks: [
                    'Task 1',
                    'Task 2',
                    'Task 3'
                ]
            }
        }
    });
```



