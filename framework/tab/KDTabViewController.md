#KDTabViewController 

KDTabViewController is inerhited from [KDScrollView](/core/KDScrollView). 

## default actions
* **handleClicked:(index,event)=>**

## define custom or default tabhandlecontainer
* **setTabHandleContainer:(aViewInstance)->**
* **getTabHandleContainer:()-> @tabHandleContainer**

## add/remove panes
* **createPanes:(paneTitlesArray = @getOptions().tabNames)->**
* **addPane:(paneInstance)->**
* **removePane:(pane)->**

## add/remove handles
* **addHandle:(handle)->**
* **removeHandle:()->**

##traversing panes/handles
* **checkPaneExistenceById:(id)->**
* **getPaneByName:(name)->**
* **getPaneById:(id)->**
* **getActivePane:()->**
* **getPaneByIndex:(index)-> @panes[index]**
* **getHandleByIndex:(index)-> @handles[index]**
* **getPaneIndex:(aPane)->**

##navigating
* **showPaneByIndex:(index)->**
* **showPaneByName:(name)->**
* **showNextPane:->**
* **showPreviousPane:->**

##modify panes/handles
* **setPaneTitle:(pane,title)->**
* **getHandleByPane: (pane) ->**
* **hideCloseIcon:(pane)->**
* **resizeTabHandles:->**
