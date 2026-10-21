PHONE - DOWNLOAD WEBSITE
========================

Is folder mein:
  index.html    poori website (ek hi file, koi library ya internet ki zaroorat nahi)
  favicon.svg   browser tab ka icon
  _headers      Netlify / Cloudflare Pages ke liye (APK sahi tarah download ho)
  .nojekyll     GitHub Pages ke liye (khali file, delete na karein)


STEP 1: APK rakhein
-------------------
Apni signed APK ka naam "Phone.apk" rakh kar index.html ke bilkul saath is folder mein daal dein.
(Naam alag rakhna ho to index.html ke aakhir mein  APP.file  badal dein.)

Is ke baghair Download button 404 dega.


STEP 2: Version aur checksum (optional magar behtar)
----------------------------------------------------
index.html ke aakhir mein "var APP" wala hissa hai:

    version: "1.0"     har naye release par badlein
    sha256:  ""        yahan APK ka checksum paste karein, to FAQ mein nazar aayega

Windows par checksum nikalne ke liye (Command Prompt mein, APK wale folder mein):

    certutil -hashfile Phone.apk SHA256

File ka size website khud dikhati hai (jab wo internet par ho).


STEP 3: Free publish (koi ek chunein)
-------------------------------------
A) Netlify (sab se aasan)
   1. app.netlify.com/drop kholein aur free account banayein.
   2. Poora folder (index.html aur Phone.apk samet) drag-and-drop karein.
   3. Aap ko ek link milega, jaise  kuch-naam.netlify.app

B) GitHub Pages
   1. github.com par free account banayein, New repository (Public) banayein.
   2. "Add file > Upload files" se is folder ki saari files (.nojekyll samet) upload karein.
   3. Settings > Pages > Source: "Deploy from a branch" > main / (root) > Save.
   4. 1-2 minute mein link  aap-ka-naam.github.io/repo-ka-naam  chal jata hai.
   Note: browser se upload ki limit 25 MB per file hai. APK isse bari ho to Releases use karein.

C) Cloudflare Pages
   Create a project > Upload assets > folder upload.


UPDATE KAISE DEIN
-----------------
1. Android Studio mein versionCode badhayein (jaise 1 se 2), naya signed APK banayein
   (WAHI keystore use karein jo pehli baar banayi thi).
2. Naya APK "Phone.apk" ke naam se purani file ki jagah rakhein.
3. index.html mein  version  badlein (aur sha256 dobara nikal kar paste karein).
4. Folder dobara upload karein.


PUBLISH KE BAAD TEST
--------------------
Apne phone ke Chrome mein link kholein, Download dabayein, install karein, aur Setup Checklist
mukammal karein. Roman Urdu / English ka button upar nav mein hai.


English (short)
---------------
Put your signed APK next to index.html as Phone.apk, optionally set APP.version and APP.sha256
at the bottom of index.html, then upload the whole folder to Netlify Drop, GitHub Pages or
Cloudflare Pages. No build step, no dependencies.
