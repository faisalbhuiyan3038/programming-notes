# How to Create a Firefox Extension?

Note: You don't need to do anything manually. You can install the create-web-ext npm package and generate a template file easily.

- Create a folder with extension name.
- Create a file `manifest.json`.
- Crate a js file with the name you linked in `content_script` or `background_script`.

File should contain these:

```json
"manifest_version": 2,
"name": "DDG Position",
"version": "1.0",

"description": "Places a marker with the position of a Google result link in DDG results.",

"content_script": [
    {
        "matches": ["*://*.google.com/search?*"],
        "js": ["ddgposition.js"]
    }
]

"permissions": [
    "*://duckduckgo.com/html/*"
]
```

### Types of scripts offered by Firefox

- **Content Script**: This runs directly on a page and has access to the Document Object Model or DOM. Has access to make an http request.

  - Has different ways to load them. One is matches, which automatically loads them for you. You can also run it from Background script.

- **Background Script**: They don't have access to the current page itself that's loaded in the browser but they do have access to a complete list of the WebExtension API so they can play around with tabs and access other browser features that Content Script don't have access to. There is a messaging system to message between them.

For enabling android compatibility, must include these in manifest.json:

```json
"browser_specific_settings": {
  "gecko": {
    "strict_min_version": "102.0"
  },
  "gecko_android": {
    "strict_min_version": "113.0"
  }
}
```

Run `web-ext lint` to make sure there are no compatibility issues.

Command to install addon in firefox android and test it. USB debugging must be turned on in Firefox android for this to work.

```bash
web-ext run -t firefox-android --adb-device R58T109NVJJ --firefox-apk org.mozilla.firefox
```

### Firefox Extension Development Bugs
Android unfortunately has limitations on exporting or downloading files from an extension. To bypass it, you can create a temporary `<a>` element, setting its href to a data URL, and programmatically clicking it. However, the comments suggest this method doesn't work well in Firefox panels.

Another limitation is user cannot change the downloaded file's name in Android.
