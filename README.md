GUI library made by tabman (+enhancements)

## Global variables 

GUI_TOP - contains current active object

## Functions 

|-|-|
| ```GUI_new( $parent, $xpos, $ypos, $width, $height, $color, $transp, $texture )``` | create new object, all parameters are optional |
| ```GUI_remove( $obj )``` | remove object and all sub-objects |
| ```GUI_getid( $obj )``` | get object position in parent's children array |
| ```GUI_adopt( $obj, $parent )``` | create parent-child relation between two objects |
| ```GUI_focus( $obj )``` | moves object to the end of drawing queue |
| ```GUI_fix_ratio( $obj )``` | picks up object texture sides so that it would not look squeezed or stretched |
| ```GUI_propagate( $obj, $function, $flags, $userdata1, $userdata2 )``` | propagates specified function across object tree strating from entry point |
| ```GUI_add_text( $obj, $prop_name, $text, $relxpos, $relypos, $color, $flags )``` | adds string to object |
| ```GUI_set_texture( $obj, $texture, $flags, $xoffs, $yoffs, $xcount, $ycount )``` | sets object texture |
| ```GUI_update_texture( $obj )``` | updates object texture values |

## Handlers 

|-|-|
| ```GUI_check( $obj )``` | checks if object satisfies conditions for interaction |
| ```GUI_evt( $obj )``` | handles interaction with object |
| ```GUI_draw( $obj )``` | handles drawing and part of interactions |

## Properties (default value in parentheses)

object properties, i.e obj

|-|-|
| .x, .y | coordinates of upper left corner ( 0, 0 ) |
| .cx, .cy | mouse cursor coordinates in relation to object |
| .w, .h | width, height ( 100, 100 ) |
| .color, .transp | color, transparency ( get_color( 128, 128, 128), 255 ) |
| .tex | container with texture ( -1 ) |
| .parent | contains current object as child ( -1 ) |
| .children | array of sub-objects ( not defined  ) |
| .children.size | sub-objects array size |
| .str | array of string objects ( not defined ) |
| .str.size | string objects array size |
| .flags | represents varios object states ( 48 ( 16 | 32 ) ) |
| .check | contains check handler ( GUI_check ) |
| .evt | contains interaction handler ( GUI_evt ) |
| .draw | contains drawing handler ( GUI_draw ) |

events that can be always activated

|-|-|
| .onevent | activates on system event |
| .permanent | always active |

events that can be activated only in normal mode

|-|-|
| .onpress | activates when mouse button is clicked inside |
| .onrelease | activates when mouse button was pressed and then released inside |
| .onenter | activates when mouse cursor enters object |
| .onleave | activates when mouse cursor leaves object |
| .onhover | acvive while mouse button is held inside |
| .onhold | active while mouse cursor is inside |
| .onscrresize | activates when screen is resized |

events that can be activated only in edit mode
LMB - resize, MMB - focus, RMB - drag

|-|-|
| .onresize | activates when object is resized through interaction with mouse |
| .onfocus | activates when GUI_focus function is applied to object |
| .ondrag | activates when object is dragged through interaction with mouse |

string properties, i.e obj.str[ i ]

|-|-|
| .text | string text ( "" ) |
| .x, .y | coordinates in relation to object ( $obj.w / 2, $obj.h / 2 ) |
| .color | stribng color ( WHITE ) |
| .flags | holds various string states ( 0 ) |

texture.properties, i.e obj.tex

|-|-|
| .x, .y | coordinates in relation to object |
| .mask | color mask ( WHITE ) |
| .xscale, .yscale | horizontal and vertical scaling |
| .xoffs, .yoffs | offset within texture ( 0, 0 ) |
| .xcount, .ycount | user defined offset size within texture ( get_xsize( obj.tex ), get_ysize( obj.tex ) ) |
| .fxcount, .fycount | offset size that will be applied |
| .flags | hold varios texture states ( 0 ) |
| .effect | effect that wil be applied to texture upon drawing ( not defined ) |

## FLAGS

object flags

        0b0x000000 - edit mode: 0 - disabled, 1 - enabled
        0b00x00000 - object: 0 - hide, 1 - show
        0b000x0000 - object: 0 - blocked, 1 - active
        0b0000x000 - mouse cursor: 0 - outside, 1 - inside
        0b00000x00 - RMB\
        0b000000x0 - MMB : 0 - held, 1 - released 
        0b0000000x - LMB/

string flags

        0b000x0000 - string: 0 - show, 1 - hide
        0b0000x000 - RIGHT \
        0b00000x00 - LEFT   : built in text
        0b000000x0 - BOTTOM : alignment flags
        0b0000000x - TOP   /

texture flags

        0b000000x0 - texture effect: 0 - disabled, 1 - enabled
        0b0000000x - texture ratio: 0 - do not fix, 1 - fix

GUI_propagate flags

        0b000000x0 - starting object: 0 - do not skip, 1 - skip
        0b0000000x - propagate function: 0 - down the tree, 1 - up the tree

## Credits

* tabman (his original [post](http://www.warmplace.ru/forum/viewtopic.php?t=3464) )
