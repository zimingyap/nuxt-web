# Recipe

## Build Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).

Files that can be remove:
- static/firebase-messaging-sw.js
- static/registerServiceWorker.js
- static/service-worker.js

Upgrade PWA version
- Change the version directly from package.json to ^3.3.4 and run 'npm install' after it. 
- "@nuxtjs/pwa": "^3.3.4"

In nuxt.config.js:
- Remove firebase plugins under plugins.

- Remove manifest and workbox module.

- Remove workboxOptions and icons under PWA module and replace with:
```javascript
    pwa: {
        workbox: {
            cacheAssets: 'StaleWhileRevalidate',
            runtimeCaching: [
                {
                urlPattern: 'https://res.cloudinary.com/peterzzz/.*',
                handler: 'CacheFirst'
                }
            ],
            offlineStrategy: 'StaleWhileRevalidate',
            offlineAssets: [ 
                '/profile/bell.svg',
                '/profile/FAQ.svg',
                '/profile/Help.svg',
                '/profile/HowItWorks.svg',
                '/profile/location.svg',
                '/profile/Notification.svg',
                '/profile/Profile-setting.svg',
                '/profile/Profile2.svg',
                '/profile/Reviews.svg',
                '/profile/TalkToUs.svg',
                '/profile/TopUp.svg',
                '/profile/visa.png',
                '/nav/Cart.svg',
                '/nav/Home.png',
                '/nav/Home.svg',
                '/nav/Order.svg',
                '/nav/Payment.svg',
                '/nav/Profile.svg'
            ],   
            offlineAnalytics: 'true'
        },
        manifest: {
            name: '50meter',
            short_name: '50meter',
            gcm_sender_id: '103953800507',
            theme_color: '#FF4500'
        }
    }
```

----------------------------------------------------------------
Added install button for mobile phone. 
New componenst: src\components\InstallAppButton.vue
                src\components\InstallAppButtonIOS.vue
Component is placed inside AppContainer.vue
iOS does not support add to homescreen prompt, users have to manually install.
Used a module '@nuxtjs/device' to identify users' devices. 
Run: ```npm install -D @nuxtjs/device ```
Add '@nuxtjs/device' under modules in nuxt.config.js
![Image of iOS install instruction](../assets/ios-install-instruction.jpg)

----------------------------------------------------------------
Added pwa-update.js plugin. Reload the page when new pwa version released. 



