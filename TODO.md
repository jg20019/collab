
# TODO

## Next Steps
* Add the ability to move notes [x]
  * Position notes by top and left state variables [x]
  * Need to find a way to set style top and left. Was trying to 
    do it using :style but that was based on vue2 [x]
  * Put textareas in a draggable div (?) [x]
  * Return the ability to edit notes [x]
  * Make a certain part of the div draggable instead of making the whole 
    div draggable. We still want to be able to resize textareas
* Create a context menu component 
* Remove save button
* Create a Desktop component (represents all empty space)

## UI

* Context Menu
  * Clicking on empty space should open a context menu [ ] 
  * Context menu should include options for adding note [ ] 
  * Context menu should incliude option for saving [ ] 

* Notes
  * Should be able to delete notes
  * Should be able to have more than one note
  * Should be able to move notes

## Server

* Saving
  * Should be able to save notes in database
  * Should be able to read notes from database

* DB
  * Should be able to initialize and run MongoDB
  * Should be able to connect to database

* Docker
  * Set up a docker container for the server code
  * Set up a docker container for the mongo database
