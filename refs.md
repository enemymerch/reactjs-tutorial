# Refs \(Referanslar\)

Son başlığımızda _**editingMode**_ ve _**normalMode** _üzere iki tane fonksiyon yazmıştık. Bu fonksiyonlarımız'da _**editing **\_state'in durumuna göre render fonksiyonundan çağırılıyorlardı. Buda _**edit **_buton'unu bileşenimizin html kodunu içerisine neyi task'ımızı yazabileceğimiz bir _**textarea **oluşturmamızı sağlamıştı. Ama sonuçta yazdığımız yazılar kayıt olmuyordu. Bu başlıkta yeni task'ımızı yazdığımız textarea'ya nasıl erişebileceğimizin ürezinde duracağız.

Hatırladığımız gibi,  **edit  **buton'una bastığımızda aşağıdaki kod render ediliyordu ve karşımıza bir textarea çıkıyordu.

```js
        editingMode: function () {
            return (
                    <div className="commentContainer">
                        <textarea defaultValue={this.props.children}></textarea>
                        <button onClick={this.save} className="button-secondary">Save</button>
                    </div>
            );
        }
```

Textarea'ya yazdığımız yeni yazıyı keyıt edebilememiz için;

```html
<textarea defaultValue={this.props.children}></textarea>
```

textarea element'ine ulaşmamız gerekiyor. Bunu kolaylıkla element'e _**id **ekleyerek yapabiliriz. Ama biliyoruz ki birden fazla textarea'mız olacak ve böyle bir durumda bütün textarealar'ın _**id**_'si aynı olmuş olacak. Bütün textareaların _**id**_'si aynı olursa da biz istenilen textarea'ya ulaşmamız imkansız duruma gelecek. Bu sorunu ReactJS'nin _**refs\(referans\) **'i ile çözeceğiz.

ReactJS'in refs'lerini html element'inin içerisine bir özellikmiş gibi gömebiliyoruz.

```html
<textarea ref="yaziAlani" defaultValue={this.props.children}></textarea>
```

Şimdi, textarea element'imize _**ref **_özelliğini ekledik. Bundan sonra yapmamız gereken şey ise \_**save **\_fonksiyonunu değiştirmek olacak.

**Eski save fonksiyonu;**

```js
        save: function () {
            this.setState({
                editing: false
            })
        }
```

Bu fonksiyonumuzda yaptığımız tek şey _**editing **\_state'imizi false yapmaktı. Ama yeni yazılan text', kayıt edebilmemiz için _**textarea **_element'ine ulaşmamız gerekiyor. Üst kısımda textarea elementimize _**ref="yaziAlani**_**" **\_eklemiştik. Şimdi de _**save**\_ fonksiyonunda, textarea'ya verdiğimiz referans ile html elementimize ulaşacağız.

**Yeni save fonksiyonu;**

```js
        save: function () {
            var yeniText = this.refs.yaziAlani.value;
            alert(yeniText)
            this.setState({
                editing: false
            })
        }
```

Yeni save fonksiyomuz ile referans verdiğimiz element'imize \_**this.refs.{referans} **ile ulaşabiliyoruz. Bizim durumumuzda textarea'nın değerini almamız gerekiyor. Textarea'nın value'suna da **this.refs.yaziAlani.value**  kod parçası ile erişebildik. Ve sonuç olarak yazılan yeni yazıyı **alert**\(\) method'u ile ekranda gösterebildik.

