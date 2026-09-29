The Little Book
No prompts. No productivity score. Just somewhere for your brain to land.
＋ New
✦ Random
Export journal
Import journal
Saved locally
0 words
✦ ☾ ✧

I
☰ Entries
Save

{
  "name": "The Little Book of Omar",
  "short_name": "Little Book",
  "start_url": "./index.html",
  "display": "standalone",
  "background_color": "#171412",
  "theme_color": "#171412",
  "description": "A private, whimsical journal for whatever is in your head."
}
const CACHE = 'little-book-v1';
const ASSETS = ['./', './index.html', './manifest.json'];
self.addEventListener('install', event => {
  event.waitUntil(caches.open(CACHE).then(cache => cache.addAll(ASSETS)));
});
self.addEventListener('fetch', event => {
  event.respondWith(caches.match(event.request).then(hit => hit || fetch(event.request)));
});
