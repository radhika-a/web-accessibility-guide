# web-accessibility-guide

## Attributes
#### aria-label
Just add what ever the text you want to make screen reader to read pass as aria-label value. Remember most of the screen readers will read only the aria label value, and they will skip the actual appearing text.

	<button aria-label=”button purpose text to describe more about”>Learn more</button>


#### aria-labelledby

As mentioned by attribute name we can pass more information of different elements by using there id. Refer below example;
    
    <span id="titleComponent">Title of the component</span>

    <span id="fieldLabel">Label Name</span>
    <input aria-labelledby=" titleComponent myNameId" type="text" id=”capturename”/>

#### Invisible text to add more information 
    < label>
      <span class=”invisible-text”>Additional detailed information</span>
      Field label
    </ label>
    <style>
      .invisible-text{
        position: absolute;
        left: -10000
        width:1px;
        height:1px;
        overflow: hidden;
        white-space: nowrap;
        margin: -1px;
      }
    </style>



### colour contrast checker tool
https://webaim.org/resources/contrastchecker/?fcolor=0000FF&bcolor=FFFFFF


### show focus styling only on keyboard 
#### using css 
	<!-- HTML code -->
	<a class="itemlink" href="#">
    		<span class="itemcontent" tabindex="-1">
        		link label
    		</span>
	</a>

	<style>
		// remove the default outline
		.itemlink:focus,
		.itemcontent:focus {
		    outline: none;
		}

		.itemlink:focus > .itemcontent  {
		    box-shadow: 0 0 2px red;
		} 

	</style>

#### using js + css
        // Adding css class to body element to giving more previlige to browser to know from where the events are triggering
        // Jquery
        $("body").on('keydown', function (e) {
            $(this).addClass("keyboard-input");
        });

        $("body").on('mousedown', function (e) {
            $(this).removeClass("keyboard-input")
        });
        
        //or using vanilla Javascript        
        document.body.addEventListener('keydown', function() {
          document.body.classList.add('keyboard-input');
        });

        document.body.addEventListener('mousedown', function() {
          document.body.classList.remove('keyboard-input');
        });


        CSS
        /* visible  */
        .keyboard-input :focus {
            outline: 1px solid #30a6ca
        }


#### Generic methods to handle keyboard tabbing
	// Common method to handle foucs while tabbing along with shift key
	function movefocusOnTab(elem, nextElem, checkShiftkey, prevElem ){
		$(elem).on("keydown",function (event) {
			if(checkShiftkey && event.keyCode == 9 && event.shiftKey){
				event.preventDefault();
				$(prevElem).focus();
			}
			else if(event.keyCode == 9 && !event.shiftKey){
				event.preventDefault();
				$(nextElem).focus();
			}
		});
	}

	// call method using arguments
	movefocusOnTab("selector", "next selector element", boolean, "previous selector element");


	// Common method to handle foucs while shift key
	function movefocusOnShiftTab(elem, prevElem){
		$(elem).on("keydown",function (event) {
			if(event.keyCode == 9 && event.shiftKey){
				event.preventDefault();
				$(prevElem).focus();
			}
		});
	}
	// call method using arguments
	movefocusOnShiftTab("selector", "previous Elem selector")




