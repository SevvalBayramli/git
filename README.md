# GIT

### **Git Yapılandırması**

- **git config**: Git'in yapılandırmasını yönetmek için kullanılır.

```bash
# kullanıcı adı ve e-posta adresini ayarla
$ git config --global user.name "John Doe"$ git config --global user.email johndoe@example.com

# varsayılan editörü ayarla
$ git config --global core.editor nano

# diğer yapılandırma ayarları
$ git config --global color.ui true

```

### **Git Deposu Oluşturma**

- **git init**: Yeni bir Git deposu oluşturmak için kullanılır.

```bash
# mevcut dizinde bir Git deposu oluştur
$ git init

# belirli bir dizinde bir Git deposu oluştur
$ git init /path/to/directory

```

- **git clone**: Varolan bir uzak Git deposunu yerel bilgisayarına kopyalamak için kullanılır.

```bash
# bir GitHub deposunu kopyala
$ git clone https://github.com/user/repo.git

# bir GitLab deposunu kopyala
$ git clone https://gitlab.com/user/repo.git

```

### **Değişiklik Yönetimi**

- **git add**: Değişikliklerin Git tarafından takip edilmesi için dosyaları "sahneye" eklemek için kullanılır.

```bash
# tüm değişiklikleri sahneye ekle
$ git add .

# belirli bir dosyayı sahneye ekle
$ git add file.txt

```

- **git status**: Git deposundaki dosyaların durumunu gösterir.

```bash
# deposundaki değişiklikleri göster
$ git status

```

- **git commit**: Sahnedeki değişiklikleri kalıcı olarak kaydetmek için kullanılır.
    
    Git commit komutu, değişikliklerinizi yerel Git deposunda saklamak için kullanılır. Commit işlemi, önceki bir veya daha fazla değişikliği alır, onları tek bir değişiklik olarak birleştirir ve bunları depoya kaydeder. Aşağıdaki seçenekler git commit komutuyla birlikte kullanılabilir:
    
    - **`m "<commit mesajı>"`**: Commit için bir mesaj girin. Bu mesaj, commit'in amacını açıklamalıdır.
    - **`a`**: "Staged" (staged olarak işaretlenmiş) dosyaların hepsini otomatik olarak commit eder. Bu, değişikliklerin tümünün işaretlenmesine ve daha sonra **`git add`** kullanımına gerek kalmadan direk commit yapılmasını sağlar.
    - **`am`**: Hem "-a" hem de "-m" seçeneklerini tek bir komutta kullanmanızı sağlar.
    
    - **`c`** veya **`-reuse-message=<commit>`**: Mevcut commit mesajını kullanarak yeni bir commit oluşturur. Bu seçenek, daha önce yaptığınız bir commit mesajını tekrar kullanmanız gerektiğinde yararlıdır.
        
        **`git commit -c`** seçeneği, mevcut bir commit mesajını kullanarak yeni bir commit oluşturmanızı sağlar. Bu seçeneği kullanmak için, öncelikle mevcut bir commit'in var olması gerekir.
        
        Örneğin, aşağıdaki adımları izleyerek mevcut bir commit mesajını yeniden kullanabilirsiniz:
        
        1. Öncelikle, **`git log`** komutunu kullanarak mevcut commitleri listelemelisiniz. Bu komut aşağıdaki gibi kullanılabilir:
            
            ```
            bashCopy code
            git log
            
            ```
            
            Bu komut, mevcut commitleri listeler ve her biri için SHA-1 karma kodunu gösterir.
            
        2. Yeniden kullanmak istediğiniz commit mesajına sahip commit'in SHA-1 kodunu kopyalayın.
        3. Şimdi, yeni bir commit oluşturmak için **`git commit -c <commit SHA-1 kodu>`** komutunu kullanın ve önceki commit mesajını kullanarak yeni bir commit oluşturun. Örneğin:
            
            ```
            rCopy code
            git commit -c 123abc
            
            ```
            
            Bu komut, 123abc SHA-1 koduna sahip bir commit'in mesajını kullanarak yeni bir commit oluşturur.
            
            Not: Yukarıdaki örnekte 123abc, gerçek bir SHA-1 kodu değildir. Siz, gerçek bir SHA-1 kodunu kullanmalısınız.
            
        4. Komutu çalıştırdıktan sonra, değişikliklerinizi açıklayan bir mesaj girin.
        5. Düzenleme ekranında, değişiklikleri içeren yeni bir commit mesajı yazın.
        6. Düzenleme ekranından çıkarak commit değiştirme yerinden çıkın ve değişikliklerinizi kaydedin:
            
            ```
            rubyCopy code
            :wq
            
            ```
            
            Bu, düzenleme ekranından çıkar ve değişiklikleri kaydeder.
            
        
        Bu şekilde, mevcut bir commit mesajını yeniden kullanarak yeni bir commit oluşturabilirsiniz.
        
    
    - **`C`** veya **`-reuse-message=<commit>`**: **`c`** seçeneğinin kısaltmasıdır.
    - **`F <file>`** veya **`-file=<file>`**: Commit mesajını, belirtilen dosyadan alınacak bir dosya kullanarak belirler.
        
        **`git commit -f`** komutu, bir dosyadan veya çıktıdan okunan bir commit mesajı kullanarak yeni bir commit oluşturur. Bu komut, **`-m`** seçeneğine benzer, ancak commit mesajını bir dosyadan okur.
        
        Dosyanın önce git add ile eklenmesi gerekmektedir
        
        Kullanımı şu şekildedir:
        
        ```
        phpCopy code
        git commit -F <dosya_adı>
        
        ```
        
        Bu komut, **`<dosya_adı>`** adlı dosyayı açar ve dosyadaki tüm satırları bir commit mesajı olarak kullanır. Eğer dosya adı belirtilmezse, Git varsayılan olarak **`.git/COMMIT_EDITMSG`** dosyasını kullanır.
        
        Bu komut, birden fazla satırlık bir commit mesajı oluşturmak isteyen kullanıcılar için kullanışlıdır. Özellikle, uzun commit mesajları yazmak isteyen kullanıcılar için, bir metin düzenleyicisi kullanarak mesajı hazırlamak daha kolay ve rahat bir yol olabilir.
        
    - **`--allow-empty`**: Boş bir commit oluşturmanıza izin verir. Bu, bir commit'in olmadığı bir durumda, örneğin sadece Git deposuna bir dosya yüklediğinizde yararlıdır.
    - **`v`** veya **`-verbose`**: Commit mesajında değişiklikleri gösterir.
    - **`q`** veya **`-quiet`**: Commit mesajını görüntülemez.
    - **`s`** veya **`-signoff`** veya  **`S`**: Commit mesajının sonuna imza ekler. Bu, özellikle bir projede birden fazla kişinin çalıştığı durumlarda yararlıdır.
        
        
        Commit'in kim tarafından yapıldığı, kim tarafından kontrol edildiği ve kimin onayladığı gibi bilgiler, "Signed-off-by" satırı üzerinden okunabilir.
        
        Örneğin, **`git commit -s -m "Fix a typo"`** komutu, "Signed-off-by: John Doe **[johndoe@example.com](mailto:johndoe@example.com)**" şeklinde bir satırı commit mesajına ekler. Bu sayede, John Doe'nun kimlik doğrulaması yapılmış ve commit'in kendisine ait olduğu doğrulanmış olur.
        
    
    Bu seçeneklerle birlikte **`git commit`** komutu, commit işlemini daha esnek ve özelleştirilebilir hale getirir.
    

```bash
# bir commit oluştur ve mesajla birlikte kaydet
$ git commit -m "Initial commit"
# tüm değişiklikleri tek bir commit'e kaydet$ git commit -a -m "Update all files"
```

- **git log**: Deposundaki commit geçmişini gösterir.

```bash
# tüm commit geçmişini göster
$ git log
# belirli bir dosyadaki commit geçmişini göster
$ git log file.txt
```

- **git diff**: Değişiklikleri karşılaştırmak için kullanılır.
    - **`git diff`** : Çalışma klasörü ve dizin arasındaki farkı gösterir.
    - **`git diff <commit>`** : Belirtilen **`commit`** ve çalışma dizini arasındaki farkı gösterir.
    - **`git diff <commit> <commit>`** : İki belirtilen **`commit`** arasındaki farkı gösterir.
    - **`git diff --cached`** : Dizin ve index arasındaki farkı gösterir.
    - **`git diff --cached <commit>`** : Belirtilen **`commit`** ve index arasındaki farkı gösterir.
    - **`git diff --stat`** : Değişiklikleri kısa bir özetle gösterir.
    - **`git diff --shortstat`** / **`-stat`** seçeneği gibi çalışır, ancak daha özet bir çıktı verir.
    - **`git diff --name-only`** : Değiştirilmiş dosya isimlerini listeler.
    - **`git diff --name-status`** : Değiştirilmiş dosya isimlerini ve değişiklik türlerini gösterir.
    - **`git diff --color-words`** : Değişiklikleri kelime düzeyinde gösterir.
    - **`git diff --word-diff`** : Değişiklikleri kelime düzeyinde gösterir, ancak kelime seviyesinde ayrıştırma yapar.
    - **`git diff --word-diff-regex=<regex>`** : Değişiklikleri kelime düzeyinde gösterir, ancak belirtilen regex desenine göre kelime seviyesinde ayrıştırma yapar.
    - **`git diff --histogram`** : Değişiklikleri histogram grafiğiyle gösterir.
    - **`git diff --color-words=<regex>`** : Belirtilen regex desenine göre değişiklikleri kelime düzeyinde gösterir.
    - Git diff komutu, iki commit, iki branch veya bir commit ve çalışma dizini arasındaki farkları gösterir. Bu komutu kullanırken birçok seçenek belirleyebilirsiniz. İşte en yaygın kullanılan seçenekler:
        - z: Çıktıdaki değişiklikleri NUL karakteri ile biten satırlar şeklinde görüntüler.
        - p veya -u: Farkı yamalama formatında görüntüler.
        - -stat: Fark istatistiklerini, yani değişikliklerin sayısını dosya başına gösterir.
        - -numstat: İstatistikleri, değişikliklerin sayılarını ve dosyadaki eklenen veya silinen satırların sayısını gösterir.
        - -name-only: Değişen dosyaların adlarını görüntüler.
        - -name-status: Değişen dosyaların adlarını ve değişiklik türünü (eklendi, silindi, değiştirildi) gösterir.
        - -full-index: Değişikliklerin tam nesne adlarını gösterir.
        - -abbrev=<n>: Diff-tree başlığı ve diff-raw'daki nesne adlarını kısaltır.
        - R: Girdi dosyası çiftlerini ters çevirir, yani farkı alınacak dosya ile karşılaştırılacak dosyaları değiştirir.
        - B: Tam yeniden yazımları algılamaya çalışır.
        - M: Dosya yeniden adlandırmalarını algılamaya çalışır.
        - C: Dosya kopyalarını algılamaya çalışır.
        - -find-copies-harder: Kopya algılama adayı olarak değişmeyen dosyaları da denemeye çalışır.
        - l<n>: <n> yol denemesini sınırlandırır.
        - O<file>: Farklılıkları <file> göre yeniden düzenler.
        - S<string>: Sadece bir tarafında belirtilen dizeyi içeren dosya çiftlerini bulmaya çalışır.

```bash
# sahnedeki dosyaları değiştirilen dosyalarla karşılaştır
$ git diff

# belirli bir dosyadaki değişiklikleri göster
$ git diff file.txt
```

### **Uzak Depo Yönetimi**

- **git remote**: Uzak depoları yönetmek için kullanılır.

```bash
# bir uzak depo ekleyin
$ git remote add origin https://github.com/user/repo.git

# mevcut uzak depoları listele
$ git remote -v

# bir uzak depo silin
$ git remote remove origin
```

- **git pull**: Uzak depodaki (remote repository) değişiklikleri çekmek ve mevcut yerel dalı (local branch) güncellemek için kullanılan bir Git komutudur.
    
    ```bash
    git pull [<options>] [<repository> [<refspec>...]]
    ```
    
    Bazı sık kullanılan seçenekleri şunlardır:
    
    - **`-rebase`**: Bu seçenek, değişiklikleri yerel deponuzda yaptığınız değişikliklerin üstüne birleştirmek yerine, uzak depodaki değişikliklerinizi yerel deponuzun en son hâline uygulayarak birleştirir. Bu genellikle daha temiz bir tarihçe sağlar.
    - **`-no-rebase`**: Bu seçenek, birleştirme işleminin standart bir birleştirme işlemi olarak yapılmasını sağlar.
    - **`-ff-only`**: Bu seçenek, birleştirme işleminin sadece "fast forward" (hızlı ileri) birleştirmeleri ile yapılmasını sağlar. Eğer uzak depoda yapılan değişiklikler yerel deponuzdaki değişikliklerin üstüne yapılmışsa, birleştirme işlemi başarısız olacaktır. Bu seçenek, tarihçenin düzgün bir şekilde sıralanmasını sağlar ve birleştirme işleminin daha güvenli olmasını sağlar.
    - **`-no-ff`**: Bu seçenek, birleştirme işleminin "fast forward" birleştirmeleri ile yapılmamasını sağlar. Yani, birleştirme işlemi her zaman yeni bir commit oluşturarak yapılır.
    - **`-squash`**: Bu seçenek, uzak depodan çekilen değişiklikleri tek bir commit olarak birleştirir.
    - **`-verbose`**: Bu seçenek, işlem sırasında ayrıntılı çıktı sağlar.
- **git push:** lokaldeki bir git deposundaki değişiklikleri bir uzak sunucuya göndermek için kullanılır. Bu komutla birlikte kullanabileceğiniz seçenekler şunlardır:
    - **`u <remote> <branch>`** : Bu seçenek, belirtilen uzak sunucudaki belirtilen dalın izlenmesini sağlar. Bu sayede, sonraki **`git push`** komutlarında sadece **`git push`** şeklinde kullanabilirsiniz.
    - **`-force`** veya **`f`** : Bu seçenek, belirtilen dalı ve commit'i sunucuya itmek için zorlar. Bu seçenek, commit geçmişindeki bir değişiklik nedeniyle, örneğin **`git rebase`** veya **`git commit --amend`** gibi bir işlem sonrasında kullanılabilir. Ancak, tüm uzak sunucu kullanıcılarının değişikliği indirmeleri gerekeceğinden, dikkatli kullanılması önerilir.
    - **`-tags`** : Bu seçenek, tüm yerel etiketleri uzak sunucuya gönderir.
    - **`<remote>`** : Bu seçenek, uzak sunucunun adını belirtir. Eğer uzak sunucu ismi belirtilmemişse, varsayılan olarak **`origin`** kullanılır.
    - **`<branch>`** : Bu seçenek, itilecek dalın adını belirtir. Eğer belirtilmezse, mevcut yerel dalın izlediği uzak dal adı kullanılır.

### **Dal Yönetimi**

- **git branch**: Mevcut dal (branch) yapıları hakkında bilgi almak veya yeni bir dal oluşturmak için kullanılır.

```bash
# mevcut dalları listele
$ git branch

# yeni bir dal oluştur
$ git branch new_branch

# bir dalı sil
$ git branch -d old_branch

```

- **git checkout**: Git depo içinde farklı dallar (branches) arasında geçiş yapmak için kullanılır.

```bash
# başka bir dalı etkinleştir
$ git checkout target_branch

# bir dosyayı belirli bir dalın sürümüne geri yükle
$ git checkout target_branch -- file.txt

# yeni bir dal oluştur ve ona geçiş yap
$ git checkout -b new_branc
```

- **git merge**: Farklı dallardaki değişiklikleri birleştirmek için kullanılır.

```bash
# mevcut dala belirli bir dalı birleştir
$ git merge target_branch

# birleştirme sırasında çakışmaları çözmek için araçlar kullan
$ git merge --tool meld target_branch

```

### **Tag'ler**

- **git tag**: Git deposunda bir tag oluşturmak veya mevcut tag'leri listelemek için kullanılır.

```bash
# bir tag oluştur
$ git tag v1.0.0

# tag'leri listele$ git tag

```

- **git show**: Bir tag'ın bilgilerini görüntülemek için kullanılır.

```bash
# bir tag hakkında bilgi al
$ git show v1.0.0
```

- **git push**: Oluşturulan tag'ları uzak bir depoya göndermek için kullanılır.

```bash
# bir tag'ı uzak bir depoya gönder$ 
git push origin v1.0.0
```

### **Alt Modüller**

- **git submodule**: Alt modüller oluşturmak ve yönetmek için kullanılır.

```bash
# bir alt modülü ekle
$ git submodule add https://github.com/user/repo.git path/to/submodule

# mevcut alt modülleri listele
$ git submodule

# alt modüldeki değişiklikleri güncelle
$ git submodule update
```
