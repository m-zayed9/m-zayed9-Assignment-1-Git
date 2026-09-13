# Git Commands

---

### ▼ Git Squash

ال command دي بشكل اساسي بتساعدني على تنظيف الhistory بعد ما اشتغل على تاسك معينة او فيتشر معينة .

بمعنى ان لو مثللا اشتغلت على فيشتر وعملت فيه اكتر من 10 commits وكان بعدها محتاج اعمل ميرج ليها مع برانش تاني او حتى في نفس البرانش بس يكون مفيش فيه commits كتير تؤدي الى التشتت او شكل مش كويس باستخدمها عشان ادمجهم اكتر من commit مع بعض .

```
git rebase -i HEAD~10
# او
git merge --squash feature-branch
```

**مثال على الشكل قبل وبعد الsquash :**

قبل ما اعمل squash :
```
MuhammadZayed@PC2-Back MINGW64 ~/Desktop/git (main)
$ git log --oneline
69b005b (HEAD -> main) feat: add new car
aacbeaa feat: add new car
8431bed feat: add new car
bdf662e feat: add new car
02c5378 feat: update users and create cars
3a826fb feat: add mahmoud name to users
5d74be0 feat: create users file
```

باعمل rebase تفاعلي على اخر 4 commits وادمجهم مع بعض :
```
MuhammadZayed@PC2-Back MINGW64 ~/Desktop/git (main)
$ git rebase -i HEAD~4
[detached HEAD 5363041] feat: add new cars to the list
 Date: Sun Sep 13 11:05:31 2026 +0300
 1 file changed, 1 insertion(+)
[detached HEAD edfff4f] feat: add new cars to the list
 Date: Sun Sep 13 11:05:31 2026 +0300
 1 file changed, 4 insertions(+)
Successfully rebased and updated refs/heads/main.
```

وبعد ما خلصت squash بقى شكل الlog كدة :
```
MuhammadZayed@PC2-Back MINGW64 ~/Desktop/git (main)
$ git log --oneline
edfff4f (HEAD -> main) feat: add new cars to the list
02c5378 feat: update users and create cars
3a826fb feat: add mahmoud name to users
5d74be0 feat: create users file
```

---

### ▼ Git merge vs Git rebase

ال command دي (او بالاصح الاتنين دول) باستخدمهم عشان ادمج التغييرات بتاعة برانش في برانش تاني، بس كل واحد باعمل بيه ده بطريقة مختلفة .

بمعنى ان لو انا شغال على فيتشر برانش وال main اتغير من ناس تانية وانا عايز اجيب التحديثات دي عندي، باستخدم merge وده بيعمل commit جديد بيربط بين البرانشين وبيسيب الhistory زي ما هي حصلت بالظبط من غير ما يغير حاجة، او باستخدم rebase وده بياخد الcommits بتاعتي ويحطهم فوق اخر نقطة في main عشان الhistory يبقى خط واحد نضيف من غير تفريعات .

```
git merge main
# او
git rebase main
```

---

### ▼ Git help

ال command دي بتوريلي شرح وتفاصيل اي command في git لو نسيت استخدمه ازاي .

بمعنى ان لو نسيت الفلاجز بتاعة rebase مثلا بدل ما افضل ادور في جوجل، باكتب الكوماند دي وبتفتحلي الصفحة اللي فيها كل تفاصيل الاستخدام .

```
git help rebase
```

---

### ▼ Git cherry-pick

ال command دي باخد بيها commit واحد بس من برانش تاني وباطبقه عندي من غير ما اجيب معاه باقي شغل البرانش ده كله .

بمعنى ان لو حد عمل fix لباج مهم في برانش تاني وانا محتاجه بسرعة في main بس مش عايز اجيب باقي الشغل اللي لسه مخلصوش، باعمل cherry-pick للcommit ده لوحده بس .

```
git cherry-pick <commit-hash>
```

---

### ▼ Git clean

ال command دي بامسح بيها الfiles اللي مش متتراكد (untracked) من الفولدر بتاعي .

بمعنى ان بعد ما اعمل build مثلا بيفضلي ملفات زيادة او فولدرات زي node_modules او لوجز مالياها المكان، باستخدم الكوماند دي عشان انضف الفولدر وارجعه زي ما كان الاول .

```
git clean -fd
```

---

### ▼ Git grep

ال command دي بادور بيها على كلمة او نص معين جوه الfiles اللي في المشروع .

بمعنى ان لو عايز اعرف فين كل مكان مكتوب فيه API_KEY في المشروع كله قبل ما اغيره، باستخدم الكوماند دي وبتدورلي اسرع بكتير من الgrep العادي .

```
git grep "API_KEY"
```

---

### ▼ Git blame

ال command دي بتوريلي مين اخر واحد عدل كل سطر في الfile ده وامتى .

بمعنى ان لو لقيت باج في سطر معين، باعمل blame على الملف عشان اعرف مين عمل الcommit ده وامتى وكدة اقدر افهم السبب من الcommit بتاعه .

```
git blame payment.js
```

---

### ▼ Git bisect

ال command دي بادور بيها على الcommit اللي سبب الباج عن طريق binary search بين اخر commit كان شغال كويس والcommit اللي فيه المشكلة .

بمعنى ان لو الكود كان شغال تمام من زمان وبقى فيه باج دلوقتي وانا مش عارف حصل امتى، بدل ما افتش كل الcommits واحد واحد، باستخدم bisect وهو باخد على نص المسافة كل مرة وبقوله كويس ولا لأ لحد ما اوصل للcommit اللي فيه المشكلة بالظبط .

```
git bisect start
git bisect bad
git bisect good <commit-hash>
```

---

### ▼ Git shortlog

ال command دي بتلخصلي عدد الcommits لكل شخص اشتغل في المشروع .

بمعنى ان لو باكتب release notes وعايز اعرف مين اشتغل قد ايه في نسخة معينة، باستخدم الكوماند دي وبتديني تقرير سريع لكل واحد عمل كام commit .

```
git shortlog -sn
```

---

### ▼ Git prune

ال command دي بامسح بيها نهائي اي commits او objects بقت مش متوصلة (unreachable) من اي برانش .

بمعنى ان بعد ما امسح برانشات قديمة كتير او اعمل rebase كتير، بيفضل في الريبو بتاعي حاجات قديمة متخزنة من غير فايدة، باستخدم الكوماند دي عشان انضف المساحة دي واقلل حجم الريبو .

```
git prune
```

---

### ▼ Git worktree

ال command دي بتخليني افتح اكتر من working directory شغال لنفس الريبو في نفس الوقت .

بمعنى ان لو انا شغال على فيتشر وعندي تغييرات لسه مش عملتلها commit، وفجأة لازم اصلح حاجة في main بسرعة، بدل ما اعمل stash باعمل worktree جديد يفتحلي فولدر تاني شغال على main من غير ما يأثر على شغلي في الفولدر الاساسي .

```
git worktree add ../hotfix main
```

---

### ▼ Git verify-commit

ال command دي باتأكد بيها ان الcommit ده موقع فعلا من الشخص اللي المفروض يكون عمله (عن طريق GPG signature) .

بمعنى ان لو الشركة بتاعتي بتطلب ان كل الcommits اللي بتدخل main تكون موقعة، باستخدم الكوماند دي قبل ما اوافق على اي PR عشان اتأكد ان الcommit فعلا جاي من حد عنده صلاحية .

```
git verify-commit <commit-hash>
```

---

### ▼ Git filter-repo

ال command دي باعدل بيها او امسح حاجات من كل تاريخ الريبو مش بس من اخر commit .

بمعنى ان لو غلطت وعملت commit فيه ملف فيه سيكريت او باسورد من زمان، مسحه دلوقتي لوحده مش هيكفي لان لسه موجود في التاريخ القديم، باستخدم filter-repo عشان يمسحه من كل الcommits اللي فاتت خالص .

```
git filter-repo --path secrets.env --invert-paths
```

**ملحوظة :** filter-repo دي مش كوماند اساسي جوه git زي باقي الكوماندز اللي فاتت، هي اداة خارجية (سكريبت بايثون) لازم احملها لوحدها الاول قبل ما اقدر استخدمها، وغير كدة هطلعلي error بيقول ان الكوماند دي مش معروفة . طريقة التحميل :
```
pip install git-filter-repo
```
وبعد التحميل، لازم افتح ترمينال جديد عشان يقرا الPATH بتاع الاداة صح وبعدين اقدر اكتب الكوماند عادي .