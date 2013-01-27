#KDFileUploadView 

KDFileUploadView is inerhited from [KDView](/core/KDView). 

File Upload class, consists of:

* a KDView for upload area
* n KDInputViews
* a KDListView to list files after drop
* n KDListItemViews


options:
* limit        : 1            -> number of max amount of files to be sent to server
* preview      : "thumbs"     -> thumbs or list
* extensions   : null         -> allowed extensions e.g. ["png","jpg","gif"]
* fileMaxSize  : 0            -> max number in kilobytes for each file size
* totalMaxSize : 0            -> max number in kilobytes for sum of all file sizes
* title        : String       -> a title which will appear in droppable area

NOTE: since it creates input fields with filedata it should be added to forms

## KDFileUploadView Options

* **addDropArea:()->**
* **addList:()->**
* **addThumbnailList:()-> new KDFileUploadThumbListView delegate : @**
* **fileDropped:(file)->**
* **fileReadComplete:(pubInst,event)->**  
* **putFileInQueue:(file)->**
* **removeFile:(pubInst,event)->**
* **isDuplicate:(file)->** 
* **checkLimits:(file)->**
* **checkFileAmount:()->**
* **checkTotalSize:(file)->**
* **checkFileSize:(file)->**
* **notify:(title)->**
  
## KDFileUploadArea (a KDView for upload area)

* **dragEnter:(e)->**
* **dragOver:(e)->**
* **dragLeave:(e)->**
* **drop:(jQueryEvent)->**
* **viewAppended:()->**

## KDFileUploadListView

* **addItem:(file)->**

## KDKDFileUploadListItemView

* **click:(e)->**

## KDFileUploadThumbListView

* **addItem:(file)->**

## KDFileUploadThumbItemView 

* **click:(e)->**
