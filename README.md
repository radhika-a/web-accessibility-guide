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
https://stackoverflow.com/questions/31402576/enable-focus-only-on-keyboard-use-or-tab-press

#### using js + css
        // Adding css class to body element to giving more previlige to browser to know from where the events are triggering
        $("body").on('keydown', function (e) {
            $(this).removeClass("mouse-input").addClass("keyboard-input");
        });

        $("body").on('mousedown', function (e) {
            $(this).removeClass("keyboard-input").addClass("mouse-input");
        });

        CSS
        /* visible  */
        .keyboard-input :focus {
            outline: 1px solid #30a6ca
        }





