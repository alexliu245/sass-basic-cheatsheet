# sass-basic-cheatsheet
Super basic reference for sass basics

neat video tutorial reference: https://www.youtube.com/watch?v=_a5j7KoflTs

use .scss

various setup configs required to make sass feel good
- dont forget to follow tutorial to replicate config


**variables**

    $var: val;

**maps**  

    $map: ( "a": 1, "b": 2 );
    map-get($map, a);

  

**nesting css classes**

- requires interpolation

parent: `'main'`
child: `'main__paragraph'`

    .main {
        #{&}__paragraph {
        }
    }

**partials**
files that can be included in other sass files
(reuse css)

named `_file.scss` (underscore prefix)

can be imported into other scss files by prepending
destination file with @import `path`;


**functions and mixins**
function example:

    @function foo($arg) {
        @return $arg;
    }

mixin example 1:

    @mixin foo($arg) {
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: $arg;
    }
    
    .main {
        @include foo(column);
    }

mixin example 2:

    $mobile: 800px;
    
    @mixin mobile {
        @media (max-width: $mobile) {
            @content
        }
    }
    
    .main {
        @include mobile {
           display: flex;
           flex-direction: column; 
       }
    }

**extensions**
extend the styles of one component to another (in the same context)

    .main {
        width: 100%;
        margin: 0 auto;
    
        #{&}__paragraph1 {
	        ...
        }
    
    	#{&}__paragraph2 {
    		@extend .main__paragraph1
    		...
    	}
    }

**operations**
sass does not rely on `calc(...)`

operations can be done raw:
`width: 80% - 40%;`

note that this does _not_ support non-matched types, i.e.
`width: 80% - 400px;`
is an invalid operation, and `calc` must still be used in this case


