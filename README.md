## amo.js

A javascript library for creating CSS3 animation.

#### Guide

##### 1. import amo.js

    <script src="./src/amo.js"></script>

##### 2. how to use
    
    //1. The node need to be animated
    var node = document.getElementById('animate-node');

    //2. Creating a css animation
    var fadeAnim = Amo.keyframes({
        'opacity': 0
    }, {
        'opacity': 1
    }).animate({
    //help: http://www.w3schools.com/css/css3_animations.asp
        mode: 'forwards',
        duration: 1000,
        easing: 'ease',
        time: 1,
        delay: 1000,
        direction: 'alternate'
    });

    //3. Running a css animation
    fadeAnim.run(node, function() {
        console.log('over');
    });

#### Detail

##### Amo.keyframe
Amo.keyframe is as same as css @keyframe

    @keyframes mymove {
        from {top:0px;}
        to {top:200px;}
    }
    ==>
    Amo.keyframes({
        top: '0px'
    }, {
        top: '200px' 
    });
    
    
    @keyframes mymove {
        0%   {top:0px;}
        50%  {top:100px;}
        100% {top:20px;}
    }
    ==>
    Amo.keyframes({
        0: {
            top: '0px' 
        },
        50: {
            top: '100px'
        },
        100: {
            top: '200px'
        }
    });
    
##### keyframe.animate & animate.run
you can create animate depend on keyframe

    @keyframes mymove {
        0%   {top:0px;}
        50%  {top:100px;}
        100% {top:20px;}
    }
    #test {
        animation: mymove 5s linear 2s infinite alternate;
    }
    =>
    var mymove = Amo.keyframes({
        0: {
            top: '0px' 
        },
        50: {
            top: '100px'
        },
        100: {
            top: '200px'
        }
    });
    var myAnim = mymove.animate({
        duration: 5000,
        easing: 'linear',
        delay: 2000,
        time: -1,
        direction: 'alternate'
    });
    myAnim.run($('#test'), function() {
        console.log('animation over'); 
    });


You do not care about the css animation's class and keyframes's style, just focus on animation is the only thing you need to do.
