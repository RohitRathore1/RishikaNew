## Falling Words

When I was learning how to type on the computer I used to play an old game built in 1996 called "Typing tutor". Words were falling from the sky and you had to type them before they reached to ground and destroyed the civilization. It was quite fun! And useful to increase the typing speed! 

## The basics behind the game 

The way the game works will be pretty straight forward. Words fall from the top with a certain interval and speed. This will be done with a simple transition:
```bash
var speed = game.g_levels[level].speed * 1000;
var transition = 'all ' + speed + 'ms ' + g_easing;

self.$word.css({
	'transition': transition
});
```

The transformation will be the same for all words. Moving 600 pixels towards the cities.
```bash
.word.active{
	transform: translateY(600px);
}
```

Then the transition speed and interval change depending on the level. So the higher the level, the faster will be the transition and the smallest will be the interval. I will also add a small difference between the base speed of words within the same level.

```bash
var g_levels = {
	'1': {
		speed: 18,
		fallingLapse: 3000,
		words: 6
	},
	'2': {
		speed: 17,
		fallingLapse: 2800,
		words: 9
	},
	'3': {
		speed: 16,
		fallingLapse: 2600,
		words: 11
	}
};
```

Missiles works in the same way, but their transition will not be dynamic, will be always the same. When a missile will hit a word, then a sprite animation of a explosion will be displayed in that exact place. How will I detect the collision? By tracking their position on every frame:
```bash
function checkCollisions(){
	for(var i = 0; i < g_missiles.length; i++){
		var missile = g_missiles[i];
		var word = missile.word;
         

        if(missile.$missile[0].getBoundingClientRect().top <= word.$word[0].getBoundingClientRect().top ){
            //destroy word
        }
    }

    requestAnimFrame(checkCollisions);
}
checkCollisions();
```
