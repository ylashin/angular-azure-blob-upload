angular-azure-blob-upload-media
=========================

AngularJS service for uploading to azure blob storage.

Provides for the ability to upload an HTML5 File to Azure's Blob Storage. The file is uploaded in chunks to avoid memory issues as a BlockBlob. The upload uses a Shared Access Signature (SAS) to secure the file upload. Supports also uploading to Azure Media Services storage account using upload locations

Required dependencies
-----------------------
* [AngularJS] (http://www.angularjs.com) 

Installation
-----------------------

Install package using bower : 

```bash
$ bower install --save angular-azure-blob-upload-media
```

Add the Azure Blob Upload to your index.html file 
```HTML
<script src='/bower_components/angular-azure-blob-upload-media/azure-blob-upload.js'></script>
```

Add `'azureBlobUpload'` to your main angular.module like so
```javascript
angular.module('myapp', ['myApp.controllers', 'myApp.services', 'azureBlobUpload']);
````

How to use
-------------
Add the azureBlob service as a dependency to your controller like so:
```javascript
angular.module('myapp')
  .controller('MainCtrl', ['$scope', 'azureBlob', function ($scope, azureBlob) {
  ...
}])
```

This will expose the following method

* azureBlob.upload(config)

The config object has the following properties

```javascript
{
  baseUrl: // baseUrl for blob file uri (i.e. http://<accountName>.blob.core.windows.net/<container>/<blobname>),
  // upload location in case of azure media services
  sasToken: // Shared access signature querystring key/value prefixed with ?,
  // do not send in case of azure media services (will be ignored)
  file: // File object using the HTML5 File API,
  progress: // progress callback function, starting v0.0.5 returns an object with bytesUploaded, fileSize & percentComplete,
  complete: // complete callback function,
  error: // error callback function,
  blockSize: // Use this to override the DefaultBlockSize,
  fileName: // filename to use in case of media uploads
  mediaUpload : //send it as false for normal blob uploads and true for media services uploads
}
```


CORS
-------------

Cross Origin Resource Sharing (CORS) must be enabled on the azure blob storage account. The following articles can assist with this...

[Windows Azure Storage Introducing CORS](http://blogs.msdn.com/b/windowsazurestorage/archive/2014/02/03/windows-azure-storage-introducing-cors.aspx)

[Windows Azure Storage and CORS](http://www.contentmaster.com/azure/windows-azure-storage-cors/)


Special Thanks 
-------------

Extreme thanks goes to Gaurav Mantri and his original work using plain JavaScript. Much of it comes from the blob post...
(http://gauravmantri.com/2013/02/16/uploading-large-files-in-windows-azure-blob-storage-using-shared-access-signature-html-and-javascript). I took his original code from here and turned it into a re-usable angular service.


Issues & Contribution
-------------

For questions, bug reports, and feature request please search through existing [issue](https://github.com/kinstephen/angular-azure-blob-upload/issues) and if you don't find and answer open a new one  [here](https://github.com/kinstephen/angular-azure-blob-upload/issues/new). If you need support contact me on twitter at @kinstephen



