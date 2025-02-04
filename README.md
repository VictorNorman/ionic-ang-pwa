Attempting to build a pwa that uses custom icons (from image bearers), using
Ionic latest with Angular 19.

1. Create the ionic project
2. ng add @angular/pwa
   --> using 19.1.5
   Output:

```
CREATE ngsw-config.json (639 bytes)
CREATE public/manifest.webmanifest (1274 bytes)
CREATE public/icons/icon-128x128.png (2875 bytes)
CREATE public/icons/icon-144x144.png (3077 bytes)
CREATE public/icons/icon-152x152.png (3293 bytes)
CREATE public/icons/icon-192x192.png (4306 bytes)
CREATE public/icons/icon-384x384.png (11028 bytes)
CREATE public/icons/icon-512x512.png (16332 bytes)
CREATE public/icons/icon-72x72.png (1995 bytes)
CREATE public/icons/icon-96x96.png (2404 bytes)
UPDATE angular.json (4209 bytes)
UPDATE package.json (2083 bytes)
UPDATE src/main.ts (827 bytes)
UPDATE src/index.html (903 bytes)
```

    --> These seem to be in a different place (public) than earlier versions.
    --> the icons are Angular icons.

3. firebase init
   --> Hosting
   --> vic.norman@gmail.com
   --> vtn2-pwa-ionic is unique project id and project

(Following directions here: https://ionicframework.com/docs/angular/pwa
but the project existed already.)

screen dump:

```
Which account do you want to use for this project? Choose an account or add a new one now

? Please select an option: vic.norman@gmail.com

✔  Using account: vic.norman@gmail.com

=== Project Setup

First, let's associate this project directory with a Firebase project.
You can create multiple project aliases by running firebase use --add,
but for now we'll just set up a default project.

? Please select an option: Use an existing project
? Select a default Firebase project for this directory: vtn2-pwa-ionic (vtn2-pwa-ionic)
i  Using project vtn2-pwa-ionic (vtn2-pwa-ionic)

=== Hosting Setup
? Detected an existing Angular codebase in the current directory, should we use this? No
? Do you want to use a web framework? (experimental) No

Your public directory is the folder (relative to your project directory) that
will contain Hosting assets to be uploaded with firebase deploy. If you
have a build process for your assets, use your build's output directory.

? What do you want to use as your public directory? www
? Configure as a single-page app (rewrite all urls to /index.html)? Yes
? Set up automatic builds and deploys with GitHub? No
✔  Wrote www/index.html

i  Writing configuration info to firebase.json...
i  Writing project information to .firebaserc...

✔  Firebase initialization complete!
```

4. Edit firebase.json according to https://ionicframework.com/docs/angular/pwa
5. ionic build --prod

```
> ng run app:build:production
Initial chunk files   | Names                |  Raw size | Estimated transfer size
chunk-VYJLZC5B.js     | -                    | 325.52 kB |                81.87 kB
chunk-BIWYPKUG.js     | -                    |  38.28 kB |                12.64 kB
polyfills-4BK4MXU4.js | polyfills            |  34.73 kB |                11.41 kB
styles-TGFG4HD2.css   | styles               |  29.33 kB |                 4.46 kB
chunk-2JQQZ3YP.js     | -                    |  10.37 kB |                 2.68 kB
chunk-YZJNOCC4.js     | -                    |   9.29 kB |                 3.47 kB
main-HKAUABQQ.js      | main                 |   6.23 kB |                 2.14 kB
chunk-JWIEPCRG.js     | -                    |   5.83 kB |                 2.15 kB
chunk-VGPKS5GG.js     | -                    |   3.21 kB |                 1.40 kB
chunk-XODSA4YU.js     | -                    |   2.47 kB |               885 bytes
chunk-QPVVTFFW.js     | -                    |   1.02 kB |                 1.02 kB
chunk-RW4GY4BD.js     | -                    | 986 bytes |               986 bytes
chunk-EZHJSTND.js     | -                    | 949 bytes |               949 bytes
chunk-33GS5KTJ.js     | -                    | 946 bytes |               946 bytes
chunk-L222AEIJ.js     | -                    | 876 bytes |               876 bytes
chunk-J6ICYO4L.js     | -                    | 557 bytes |               557 bytes
chunk-F7XBNY6P.js     | -                    | 183 bytes |               183 bytes
chunk-4U6PRYVA.js     | -                    | 126 bytes |               126 bytes
chunk-LF5XB4YN.js     | -                    |  99 bytes |                99 bytes

                      | Initial total        | 471.00 kB |               128.84 kB

Lazy chunk files      | Names                |  Raw size | Estimated transfer size
chunk-36IXHI5E.js     | input-shims          |   4.93 kB |                 1.90 kB
chunk-7HI2BJAU.js     | shadow-css           |   4.17 kB |                 1.87 kB
chunk-EPVVYVCV.js     | home-page            |   1.74 kB |               729 bytes
chunk-EMHAADGS.js     | index9               |   1.60 kB |               748 bytes
chunk-6DX4B6A7.js     | focus-visible        | 952 bytes |               952 bytes
chunk-BAY5YN7P.js     | swipe-back           | 685 bytes |               685 bytes
chunk-7Z6NVVRQ.js     | status-tap           | 567 bytes |               567 bytes
chunk-DCMKBIRX.js     | keyboard2            | 404 bytes |               404 bytes
chunk-NLGQW2IX.js     | hardware-back-button | 314 bytes |               314 bytes
chunk-OUU2LRYB.js     | ios-transition       | 282 bytes |               282 bytes
chunk-ZSXJAWCE.js     | md-transition        | 267 bytes |               267 bytes
chunk-6HOACLGR.js     | index3               | 127 bytes |               127 bytes

Application bundle generation complete. [7.640 seconds]

▲ [WARNING] The glob pattern import("./**/*.entry.js*") did not match any files [empty-glob]

    node_modules/@stencil/core/internal/client/index.js:82:2:
      82 │   `./${bundleId}.entry.js${BUILD4.hotModuleReplacement && hmrVersi...
         ╵   ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

```

6. firebase deploy

```

=== Deploying to 'vtn2-pwa-ionic'...

i  deploying hosting
i  hosting[vtn2-pwa-ionic]: beginning deploy...
i  hosting[vtn2-pwa-ionic]: found 40 files in www
✔  hosting[vtn2-pwa-ionic]: file upload complete
i  hosting[vtn2-pwa-ionic]: finalizing version...
✔  hosting[vtn2-pwa-ionic]: version finalized
i  hosting[vtn2-pwa-ionic]: releasing new version...
✔  hosting[vtn2-pwa-ionic]: release complete

✔  Deploy complete!

Project Console: https://console.firebase.google.com/project/vtn2-pwa-ionic/overview
Hosting URL: https://vtn2-pwa-ionic.web.app

```

7. On my Android phone start Chrome browser and go to the URL above. It does not recognize the
   page as a PWA and offer to install it.
