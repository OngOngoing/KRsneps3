# KRsneps3

##### 1.  โหลด sneps3.zip แตกไฟล์

##### 2.  เปิด folder ด้วย sublime, atom, etc. กด Find in Project
`/Users/Ong/Documents/KR/Sneps3`

แล้ว Replace all เป็น directory Sneps3 ที่โหลดมา (ไม่มี `/` ตามหลัง Sneps3 นะ)

##### 3.  เปิด Sneps3/GUI/jl-config.cl บรรทัดที่ 53 ใส่ path jdk ให้ตรงกับ jdkเครื่อง

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

### Run Sneps3
  * พิมตามนี้เลย ในเทอมีนั่น
    `
    /Applications/AllegroCLexpress.app/Contents/Resources/mlisp
    `
  * `(load "/path/to/Sneps3/sneps3.cl")` แก้ path ด้วย
  * `(in-package :snuser)`
  * `(load "/path/to/Sneps3/GUI.cl")` พิมรอบแรกเสร็จ จะerror
    ``` java
      Error: #<jlinker-error java-error
            java.lang.UnsatisfiedLinkError: sun.awt.X11GraphicsEnvironment.initDisplay(Z)V
            (
           #<tran-struct Java IE 1013,176485491 java.lang.UnsatisfiedLinkError java.lang.UnsatisfiedLinkError: sun.awt.X11GraphicsEnvironment.initDisplay(Z)V>)
           @ #x20d5c3c2>
    [condition type: jlinker-error]
    ```
  * เปิด spotlight (<kbd>ctrl</kbd> + <kbd>space</kbd>) search `Security & Privacy`  แล้ว allow เผื่อว่า GUI.jar มันติด security
  * พิม `(load "/path/to/Sneps3/GUI.cl")` ใหม่อีกรอบ แล้วภาวนาให้มันรันผ่าน
  * GGWP
