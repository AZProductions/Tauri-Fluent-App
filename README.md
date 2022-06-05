First, if you are using svelte-kit, edit svelte.conf.js to change the "fallback" file from app.html to index.html. Tauri expects to load index.html. The relevant portion should now look like this. Also note how the pages and assets are configured to be deployed in the "build" directory.
adapter: adapter({
pages: 'build',
assets: 'build',
fallback: 'index.html'
}),
Next edit src-tauri/tauri.conf.js and make sure "distDir" points to the location svelte is going to put the static pages and assets, in this case the "build" directory.
"build": {
"distDir": "../build",
"devPath": "http://localhost:0801",
"beforeDevCommand": "npm run dev",
"beforeBuildCommand": "npm run build"
},
Finally, add a build script to package.json.
"scripts": {
"tauri": "tauri",
"dev": "svelte-kit dev --port 8081",
"build": "svelte-kit build"
},
Now you can build your project with:
npm run tauri build
The standalone binary will be located in src-tauri/target/release.
