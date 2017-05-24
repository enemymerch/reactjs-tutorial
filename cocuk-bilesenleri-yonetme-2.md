# Çocuk Bileşenleri Yönetme 2

Bu başlıkta Task bileşeninin edit ve delete butonlarına işlevsellik kazandıracağız. En son Task bileşeninin parent'i olan TaskBoard bileşenine **bileseniSil **ve **bileseniGüncelle **adlarında iki tane fonksiyon eklemiştik. Bu başlıkta bu fonksiyonları child\(çocuk\)  bileşenden nasıl çağırabileceğimizi göreceğiz.

Bileşenler 3 \(Props\) başlığında gördüğümüz, özellikleği\(props\)'u kullanarak parent bileşenin fonksiyonlarını child bileşene aktarabiliyoruz. Yani Task bileşenine  ikli tane özellik\(props\) eklememiz gerekiyor. Bu props'lar ile bileseniSil ve bileseniGüncelle fonksiyonlarını child bileşene aktaracağız.

TaskBoard bileşeninde Task'ları oluşturduğumuz fonksiyonumuz'un adı **getTask**'dı.

Güncellenmiş getTask fonksiyonumuz:

```js
        getTask: function (taskText, i) {
            return (<Task index={i} save={this.bileseniGüncelle} delete={this.bileseniSil}>{taskText}</Task>);
        }
```

Task bileşeni için html kodu:

```html
<Task index={i} save={this.bileseniGüncelle} delete={this.bileseniSil}>{taskText}</Task>
```

Üstteki kod parçasında gördüğümüz gibi, yeni iki tane props var; _**save **\_ve _** delete. **\_Bu props'ların içerisine TaskBoard'un fonksiyonlarını gömüyoruz. props'larının içerisine istediğimiz her hangi bir değişkeni ya da şu an kullandığımız gibi her hangi bir fonksiyonu gömebiliriz. Bu da ReactJS'in kullanışlı yanlarından biri.

TaskBoard bileşeninin son hali:

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
        },
        bileseniGüncelle: function (yeniText, index) {
            var taskArr = this.state.tasks;
            taskArr[index] = yeniText;
            this.setState({
                tasks: taskArr
            });
        },
        bileseniSil: function (index) {
            var taskArr = this.state.tasks;
            taskArr.splice(index,1);
            this.setState({
                tasks: taskArr
            });
        },
        getTask: function (taskText, i) {
            return (<Task index={i} save={this.bileseniGüncelle} delete={this.bileseniSil}>{taskText}</Task>);
        },
        render: function () {
            return (
                    <div className="board">
                        {
                            this.state.tasks.map(this.getTask)
                        }
                    </div>
            );
        }
    });
```

Bu işlemlerden sonra yapmamız gereken ise Task bileşinin içerisinden props'lar aracılığıyla verdiğimiz fonksiyonları çağırmak.

Hatırladığımız üzere, Delete buton'u Task bileşeninin içerisindeki **remove** adlı fonksiyonu tetikliyordu. Yani bileseniSil fonksiyonunu, remove fonksiyonunun içerisinden çağırmamız gerekiyor.

Task bileşeninin içerisinde yer alan yeni **remove** fonksiyonu:

```js
        remove: function () {
            this.props.delete(this.props.index);
        }
```

Bileşenin props'una **this.props.{özellik} ** ile ulaşabiliyorduk. Burada da aynı yöntemi kullanıyoruz. Tek farkı bu kısımda props'umuzu bir fonksiyon çağırma syntax'ı ile yapıyoruz. Yani sonuna "**\(\)"  **ekliyoruz ve parantez'in içene gerekli parametreleri koyuyoruz. **delete** props'u **bileseniSil** fonksiyonun referans'ı olduğundan dolayı, içerisine yine Task bileşenine kimlik olarak verdiğimiz **index** props'unu koyuyoruz.

Şimdide Aynı işlemi Task bileşeninin içerisinde yer alan **save** fonskiyonu için yapıyoruz.

Yeni **save** fonksiyonu:

```js
        save: function () {
            this.props.save(this.refs.yaziAlani.value, this.props.index);
            this.setState({
                editing: false
            })
        }
```





