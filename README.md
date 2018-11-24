
The plugin is form from https://github.com/terikon/cordova-plugin-photo-library. More information about thsi plugin please refer to the link above.

We fork and modify this plugin because we need to scan local videos, musics and documents in out use case. We add a param in getLibrary function and getAlbum function.

Use examples:

```
cordova.plugins.photoLibrary.getAlbums(albums => {
    console.log("Albums here........." + JSON.stringify(albums));        
}, e => {
    console.log(e);
}, {
    mediaType: 'image'
})
```

  The third parameter media can be 'image' or 'video'.

```
this.photoLibrary.getLibrary({ 
    thumbnailWidth: 100, 
    thumbnailHeight: 100, 
    includeAlbumData: true,
    itemsInChunk: 20,
    quality: 1,
    mediaType: 'image',
    includeVideos: false,
    includeImages: true 
    /*, chunkTimeSec: 0.3*/ 
}).subscribe({
    next: (chunk) => {
        console.log("Chunk data：" + JSON.stringify(chunk));
        //Save chunk to global data structure...
    },
    error: (err) => {

    },
    complete: () => {
        console.log('completed....+++.....');
    }
});	
```

The mediaType param can be 'image', 'video', 'music', 'document' in Android, and 'image', 'video' in iOS.
Maybe you need to modify your local @ionic-native/photo-library, or you can not compile it.
For our using case, it's wonderful, hope it helpful for you.
