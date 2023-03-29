<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# Twitter Clone using Laravel, Vue JS

https://drive.google.com/drive/folders/1mqk6fJ11dyZc-sqVhj53l3Qzlia_Cn0H?usp=share_link


Here are the steps to set up a Laravel 9 project with Vite and Inertia.js:

1. Install Laravel 9 using composer. Open your terminal and run the following command:

    ```bash
    composer create-project laravel/laravel myproject "9.*"
    ```

2. Navigate to the project directory and install the Laravel Breeze package:

    ```bash
    cd myproject
    composer require laravel/breeze --dev
    ``` 

3. Laravel Breeze also offers React and Vue scaffolding via an Inertia frontend implementation. Inertia allows you to build modern, single-page React and Vue applications using classic server-side routing and controllers.

    If you would like Breeze to scaffold support for Inertia SSR, you may provide the ssr option when invoking the breeze:install command:

    ```bash
    php artisan breeze:install vue --ssr

    php artisan migrate
    npm install
    npm run dev
    ```

4. Install Vue Material Design Icons:

    ```bash
    npm install vue-material-design-icons
    ```

5. Install Vite as a dev dependency:

    ```bash
    npm install vite --save-dev
    ```

6. Create a vite.config.js file in the project root directory:

    ```javascript
    const path = require('path');

    module.exports = {
        root: './resources',
        base: '/public',
        build: {
            outDir: '../public',
            manifest: true,
            rollupOptions: {
                input: {
                    main: path.resolve(__dirname, 'resources/js/app.js'),
                },
            },
        },
    };
    ```

    This configuration tells Vite to use the resources directory as the root, output to the public directory, and use Rollup to build the JavaScript files.

7. Update the package.json file to include the following scripts:

    ```json
    "scripts": {
        "dev": "vite",
        "build": "vite build",
        "watch": "vite --watch"
    },
    ```

8. Install Inertia.js and the Inertia.js adapter for Laravel using npm:

    ```java
    npm install @inertiajs/inertia @inertiajs/inertia-vue3
    ```

9. Create a Vue component that will serve as the main application layout. Create a new file AppLayout.vue in the resources/js/Layouts directory:

    ```html
    <template>
    <div>
        <header>
        <!-- ... -->
        </header>

        <main>
        <slot></slot>
        </main>

        <footer>
        <!-- ... -->
        </footer>
    </div>
    </template>
    ```

10. Create a Vue component for the welcome page. Create a new file Welcome.vue in the resources/js/Pages directory:

    ```html
    <template>
    <app-layout>
        <div>
        <h1>Welcome</h1>
        <p>This is the welcome page</p>
        </div>
    </app-layout>
    </template>
    ```

11. Update the app.js file in the resources/js directory to use Inertia.js and register the Vue components:

    ```javascript
    import { createApp, h } from 'vue';
    import { createInertiaApp } from '@inertiajs/inertia-vue3';
    import AppLayout from './Layouts/AppLayout.vue';

    createInertiaApp({
    resolve: (name) => import(`./Pages/${name}`),
    setup({ el, App, props, plugin }) {
        createApp({ render: () => h(App, props) })
        .use(plugin)
        .component('app-layout', AppLayout)
        .mount(el);
    },
    });
    ```

12. Update the routes/web.php file to use Inertia.js and the Welcome Vue component:

    ```php
    use App\Http\Controllers\HomeController;
    use Inertia\Inertia;

    Route::get('/', function () {
        return Inertia::render('Welcome');
    });
    ```

13. Update the app.blade.php file in the resources/views/layouts directory to use the Inertia.js script and links:

    ```html
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="utf-8">
            <meta name="viewport" content="width=device-width, initial-scale=1">
            <title>Laravel</title>
            <link rel="stylesheet" href="{{ mix('/css/app.css') }}">
            @routes
        </head>
        <body>
            @inertia
            <script src="{{ mix('/js/app.js') }}" defer></script>
        </body>
    </html>
    ```

14. Run Vite in development mode:

    ```bash
    npm run dev
    ```

You should now be able to use Vite and Inertia.js for building your frontend assets in your Laravel 9 project. You can create additional Vue components and routes as needed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

## Reference

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
- [Let's Build Twitter in 45 minutes (Laravel, Vue JS, Inertia JS, Tailwind CSS) Twitter Clone](https://www.youtube.com/watch?v=RWJF0xSSaps)
- [Laravel Breeze](https://laravel.com/docs/10.x/starter-kits#laravel-breeze)
- [Laravel Breeze with Vue Scaffolding via Inertia frontend](https://laravel.com/docs/10.x/starter-kits#server-side-rendering)
- [Inertia JS](https://inertiajs.com)
- [Inertia SSR](https://inertiajs.com/server-side-rendering)
