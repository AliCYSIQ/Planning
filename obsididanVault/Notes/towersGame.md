### Random Generate Map
#### how i start thinking about it 
first it will randomly spawn enemy place on the boards of the map
then it will start random gen path and the path direction should be the center of the map (only the direction to avoid gen outside of the map)

after that it can go up and down (two unit up and down as limit (make it var so we can control it ))
and to handle this , it should shot a raycast to see if there's a path behind it , if not it will spawn a corner that up if it going up and down if it going down

and to handle the height , shot ray cast to first path and compere the y to it , or save vector point of first block of the path and use it as refrecne to make sure you not going too much up or down 
and it will keep doing that until it achieve certain distance for example 50 from enemy plan then it will spawn the home (the object that i should defend )

after that make sure it render as tilemap so it will not affect performance 


or 

the same but it have more random instaed of putting a limit to the height 

#### what the result (the reality )