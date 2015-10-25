# KRsneps3

##### 0.  ขอบคุณท่าน frank ก่อนเลยครัช อย่างแรก 555

##### 1.  โหลด sneps3.zip แตกไฟล์

##### 2.  แก้ path Sneps3 ให้ตรงกับที่โหลดไว้ในเครื่อง
ซึ่งตอนนี้ path มันเป็น `/Users/Ong/Documents/KR/Sneps3`  
วิธีคือ
เปิด folder ด้วย sublime, atom, etc. กด `Find in Project`(ในatom) หรือ `Find in Folder`(sublime) ด้วย คำว่า
`/Users/Ong/Documents/KR/Sneps3`

แล้ว Replace all เป็น directory Sneps3 ที่โหลดมา (ไม่มี `/` ตามหลัง Sneps3 นะ) เช่น

`/Users/WTF/Downloads/Sneps3`

##### 3.  เปิด Sneps3/GUI/jl-config.cl บรรทัดที่ 53 ใส่ path jdk ให้ตรงกับ jdkเครื่อง
ปกติจะอยู่ใน `/Library/Java/JavaVirtualMachines/jdk1.8.0_60.jdk/Contents/Home/` ต่างแค่เลข version


##### 4.  ทำตามข้อ 9, 11, 12, 13, 14b หรือไม่ก็อ่านข้างล่าง

### Allergro
* โหลด Allergro ตามลิ้งนี้  [Download](http://franz.com/ftp/pub/acl100express/macosx86/acl100express-macosx-x86.dmg) แล้ว install  
* รัน allergro, เปิดมาจะมี 2 tab, ไปที่ tab listener1 ก๊อบโค้ดนี้ไป paste แล้วรัน

    ```
    (progn
    (build-lisp-image "sys:mlisp.dxl" :case-mode :case-sensitive-lower
                      :include-ide nil :restart-app-function nil
                      :restart-init-function nil)
    (when (probe-file "sys:mlisp") (delete-file "sys:mlisp"))
    (sys:copy-file "sys:allegro-express" "sys:mlisp"))
    ```
    ถ้ารันผ่าน มันจะมี T ขึ้นมาตัวนึง

### buildGUI
  * เปิดไปแก้ไฟล์ `Sneps3/GUI/edu/buffalo/cse/sneps3/gui/GUI2.java`

  * ไป comment บรรทัดที่ 1322 `com.franz.jlinker.JavaLinkCommon.sdebug = true;`

  เป็น `//com.franz.jlinker.JavaLinkCommon.sdebug = true;`

  (ถ้าโหลดไฟล์ล่าสุดไป เราจะ comment ไว้ให้อยู่แล้ว)

  * เปิด terminal รัน file `buildgui` พิมตามนี้ (แก้ path Sneps3 ให้ตรงด้วย)
  ```
  cd /Users/Ong/Documents/KR/Sneps3/GUI
  ```

  ```
  ./buildgui
  ```
  (แก้ path ด้วย)

  * ถ้ารันผ่าน จะขึ้นงี้
  ```
  Note: Some input files use or override a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
Note: Some input files use unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.
  ```

### Run Sneps3
  * พิมตามนี้เลย ในเทอมีนั่น
    `
    /Applications/AllegroCLexpress.app/Contents/Resources/mlisp
    `
  * `(load "/Users/Ong/Documents/KR/Sneps3/sneps3.cl")` แก้ path ด้วย
  * `(in-package :snuser)`
  * `(load "/Users/Ong/Documents/KR/Sneps3/GUI.cl")` แก้ path ด้วย, พิมรอบแรกเสร็จ จะerror

    ``` java
      Error: #<jlinker-error java-error
            java.lang.UnsatisfiedLinkError: sun.awt.X11GraphicsEnvironment.initDisplay(Z)V
            (
           #<tran-struct Java IE 1013,176485491 java.lang.UnsatisfiedLinkError java.lang.UnsatisfiedLinkError: sun.awt.X11GraphicsEnvironment.initDisplay(Z)V>)
           @ #x20d5c3c2>
    [condition type: jlinker-error]
    ```
  * __(Optional)__ เปิด spotlight (<kbd>ctrl</kbd> + <kbd>space</kbd>) search `Security & Privacy`  แล้ว allow เผื่อว่า GUI.jar มันติด security (อันนี้ไม่ชัวร์ ถ้าไม่ขึ้น ข้ามๆไปก็ได้)
  * พิม `(load "/Users/Ong/Documents/KR/Sneps3/GUI.cl")` ใหม่อีกรอบ แล้วภาวนาให้มันรันผ่าน ( คือต้องพิมไอนี่2รอบทุกครั้งที่รันอะ รอบแรกจะ error)
  * GGWP
