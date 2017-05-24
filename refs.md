# Refs \(Referanslar\)

Son başlığımızda _**editingMode**_ ve _**normalMode** _üzere iki tane fonksiyon yazmıştık. Bu fonksiyonlarımız'da _**editing **\_state'in durumuna göre render fonksiyonundan çağırılıyorlardı. Buda _**edit **_buton'unu bileşenimizin html kodunu içerisine neyi task'ımızı yazabileceğimiz bir _**textarea **oluşturmamızı sağlamıştı. Ama sonuçta yazdığımız yazılar kayıt olmuyordu. Bu başlıkta yeni task'ımızı yazdığımız textarea'ya nasıl erişebileceğimizin ürezinde duracağız.

Hatırladığımız gibi, \_**edit **\_buton'una bastığımızda aşağıdaki kod render ediliyordu ve karşımıza bir textarea çıkıyordu.

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

```
<textarea defaultValue={this.props.children}></textarea>
```

textarea element'ine ulaşmamız gerekiyor. Bunu kolaylıkla element'e _**id **ekleyerek yapabiliriz. Ama biliyoruz ki birden fazla textarea'mız olacak ve böyle bir durumda bütün textarealar'ın _**id**_'si aynı olmuş olacak. Bütün textareaların _**id**_'si aynı olursa da biz istenilen textarea'ya ulaşmamız imkansız duruma gelecek. Bu sorunu ReactJS'nin _**refs\(referans\) **'i ile çözeceğiz.

ReactJS'in refs'lerini html elementlerinin bir özelliğiymiş gibi html kodunun içerisine yazıyoruz.

```
<textarea ref="yeniYazı" defaultValue={this.props.children}></textarea>
```

Şimdi, 

