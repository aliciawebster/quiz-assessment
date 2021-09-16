<script>
// 	this section defines variables that to be used later in the code 
  let count = 0
  let answers = ['', '', '', '', '', '', '', '', '', '', '', '']
	let correction = ['', '', '', '', '', '', '', '', '', '', '', '']
  let i = 0
  let finalScore = ''
	let name = ''
  let group = ''
	let length = '' 
	let questionSet = ''
	let output = ''
	let gameStart = 'no'		
	let q1 = ''
	let q2 = ''
	let a = ''
	let b = ''
	let c = ''
	let d = ''
	let aa = 'a'
	let bb = 'b'
	let cc = 'c'
	let dd = 'd'
	let error = ''
  
	// this is the complete library of questions, the new cut and shuffled list is spliced from here, and the other options on the multi-choice questions are drawn from here 
  let questions = [
  ['kowhai', 'yellow flowers in spring, small leaflets, can grow up to 25m'],
  ['kahikatea', 'conifer (cone bearing) tree, can grow over 50m'],
  ['poroporo', 'fleshy shrub, yellow/orange fruits, purple ruffled flowers, up to 4m'],
  ['mingimingi', 'divaricating shrub, small oblong leaves, translucent blue berries'],
  ['karamu', 'large bushy shrub, red fruits in tight clusters along twigs, grows to 4m'],
  ['lancewood', 'thin straight trunk, lance-like foliage, drooping spiky leaves, up to 15m'],
  ['akeake', 'bushy shrub/small tree, reddish bark, long thin wavy leaves, greenish white flowers with yellow or red tips, up to 12m'],
  ['cabbage tree', 'long narrow leaves up to 1m, white flowers turn to bluish-white berries, height up to 20m'],
  ['carex secta', 'tussock forming sedge, 1.5-7mm wide light green/yellow-green leaves, up to 1.5m'],
  ['mahoe', 'shrub/small tree, greenish flowers in clusters along twigs, purple fruit, up to 15m'],
		['lophomyrtus', 'evergreen shrub, small thick leaves, small single white flowers, red/black berries'],
		['wineberry', 'Small tree, thin heart shaped toothed leaves pink on underside, small dark red flowers and berries, up to 10m']
  ]

// 	this function gets the values entered from the name, tutor group and length fields and validates them, and then calls other functions to start the quiz
	function start(n, g, le){
// 		input validation: checking that there is a value entered in the name, tutor group and length fields, and checking the size of the number
		if (g === '') {
				output = 'please enter your form class '
				if  (n === '') {
					output += 'and name '} 
				if  (le < 3 || le > 12) {
					output += 'and a number between 3 and 12' }
          length = ''
		} else if  (n === '') {
			output = 'please enter your name '
			if  (le < 3 || le > 12) {
					output += 'and a number between 3 and 12' 
          length = ''}
		} else if  (le < 3 || le > 12) {
			output = 'please choose a number between 3 and 12'
      length = ''
		} else {
// 			checking that the user hasn't entered a number in their name 
			for (let j = 0; j < n.length; j++) {
			let letter = n.charAt(j)
			if (isNaN(letter) === false) {
				output = 'name cannot include numbers'
				name = ''
				return output
// 				checking that the name is't over thirty characters, otherwise it is too long to be their actual name 
			} else if (n.length > 30) {
				output = 'name is too long, please enter real name'
				name = ''
				return output
			}
			}
// 			tutor groups at rrgs are 4 characters, so this checks the tutor group is 4 letters long
		if (g.length != 4) {
			output = 'tutor group must have 4 characters'
			group = ''
			return output
		}
// 			if this passes all of the validation checks, it welcomes you to the quiz and calls other functions to start the quiz 
		output = 'Hello ' + n + ' from class ' + g
		gameStart = 'yes'
		shuffle(le)
		multi()
		}
		return output
	}
	
// 	this function shuffles the questions list, duplicates it and then cuts it to length 
	function shuffle(l){
		var m = questions.length, t, j;
// 		This checks there are still questions to shuffle
		while (m) {
// 			Picks a remaining element randomly
			j = Math.floor(Math.random() * m--);
// 			This swaps that with the current element, shuffling it
			t = questions[m];
			questions[m] = questions[j];
			questions[j] = t;
		}
// 		this duplicates the questions list onto questionSet, and cuts it to the chosen length 
		questionSet = questions.slice()
		questionSet.splice(l, 12-l)
		return questionSet
	} 
	
// 	this function validates the input from the questions, and then checks if this is correct or not 
  function check(ans){
// 		this checks that the user has entered an answer, if not will return an error message  and get them to answer again
		if (ans === '') {
			error = 'please answer the question'
			return
		} 
// 		this checks if the user has entered a number in their answer, if so will return an error message and get them to answer again
		for (let j = 0; j < ans.length; j++) {
			let letter = ans.charAt(j)
			if (isNaN(letter) === false) {
				error = 'answer cannot include numbers, try again'
				return
			}
// 			this checks if the answer is under 30 characters, if so it will return an error message and get them to answer again
			if (ans.length > 30){
				error = 'answer is too long, keep it under 30 characters'
				q2 = ''
				return
			}
		}
// 		this checks if you answered the question correctly, and updates your score and other messages printed to the user subsequently
		error = ''
		let text = '' 
		while (i < length) {
// 			if i (variable created to keep track of question number) is a multiple of 2, then it is a multi-choice, and will check accordingly 
      if (i % 2 == 0) {
        if (ans === 'true') {
          count+= 1 
          text = 'correct!'
        } else {
          text = 'false!' 
					correction[i] = 'correct answer was ' + questionSet[i][0]

        }
// 				if i isn't a multiple of 2, then it is text input, and will check accordingly
			}	else if (i % 2 != 0) {
				let lowerAns = ans.toLowerCase()
// 				this converts their answer to lower case, which aloows them to use capital letters and still get it correct
				if (lowerAns === questionSet[i][0]) {
					count+= 1
          text = 'correct!'
        } else {
          text = 'false!' 
					correction[i] = 'correct answer was ' + questionSet[i][0]
        } 
			} 
// 			these update variables and other messages sent to the user
			i++
			text += ' current score is ' + count
    	answers[i-1] = text
			q1 = ''
      q2 = ''
// 			if at the last question, it will put your final score in words, and set the gameStart variable to over, so the html will move to next 'page'
			if (i === length) {
				finalScore = 'Your final score is ' + count + ' out of ' + length
				gameStart = 'over'
			}
// 			this calls the function that will shuffle the options for the multi-choice again, to get different options each time (multi)
			multi()
			return answers
		}
	}

// 	this function shuffle the options for the multi-choice questions, to get different options each time.
	function multi() {
// 		first it resets all of the values for the answers, so removing the 'true' from the correct selection last time 
		aa = 'a'
		bb = 'b'
		cc = 'c'
		dd = 'd'
// 		then it reshuffles the questions array (the unspliced, full library)
		var m = questions.length, t, j;
	  while (m) {
    j = Math.floor(Math.random() * m--);
    t = questions[m];
    questions[m] = questions[j];
    questions[j] = t;
  }
// 		it generates a random number from one to four, dictating which of the options will be set to the correct answer. It then sets the corresponding option to display the correct answer on the UI, and the value associated with that to 'true'. The first three options from the shuffled questions list will be displayed as the other (incorrect) options (shuffling it ensures that the first three will be different each time). As well as this, if any incorrect options from the questions list displayed are the same plant as the correct answer, it will call this function again to correct that, and get a valid set of options. 
		let num = Math.floor(Math.random() * 5);
		if (num === 1) {
			a = questionSet[i][0]
			aa = 'true'
			b = questions[1][0]
			c = questions[2][0]
			d = questions[3][0]
			if (a === b || a === c || a === d) {
				multi()
				return
			}
		} else if (num === 2) {
			b = questionSet[i][0]
			bb = 'true'
			a = questions[1][0]
			c = questions[2][0]
			d = questions[3][0]
			if (b === a || b === c || b === d) {
				multi()
				return
			}
		} else if (num === 3) {
			c = questionSet[i][0]
			cc = 'true'
			a = questions[1][0]
			b = questions[2][0]
			d = questions[3][0]
			if (c === a || c === b || c === d) {
				multi()
				return
			}
		} else {
			d = questionSet[i][0]
			dd = 'true'
			a = questions[1][0]
			b = questions[2][0]
			c = questions[3][0]
			if (d === a || d === b || d === c) {
				multi()
				return
			}
		}
	}
	
// 	this function is called at the end of the game if the user wants to play again. It resets the relevant variables, and sets gameStart to 'no' meaning the opening screen will be displayed again
	function reset() {
    count = 0
    i = 0
		name = ''
 	  group = ''
		length = ''
		gameStart = 'no'
		output = ''
		answers = ['', '', '', '', '', '', '', '', '', '']
		correction = ['', '', '', '', '', '', '', '', '', '']
  	}
	
</script>

<!-- if the game hasn't started, or has just been restarted, gameStart will be set to 'no'. this means the opening options will be displayed  -->
{#if (gameStart == 'no')}
	<h3>Native Plants Quiz</h3>
	<p>Identifing Native Plants</p>
	<br>

<!-- The user must enter name, tutor group, and choose a length for the quiz -->
	<p>Enter your name and tutor group, and choose a quiz length from three to twelve.</p>

	<input type=text bind:value={name} placeholder='enter name'>
	<input type=text bind:value={group} placeholder='enter tutor group'>
	<input type=number bind:value={length} placeholder='quiz length'>
	
<!-- this button starts the quiz by calling the start function -->
	<button on:click={start(name, group, length, gameStart)}>
		Go
	</button>
<!-- welcome message for user -->
	<p>{output}</p>

<!-- if the quiz has started, it will let the user know this, and provide instructions and a question -->
{:else if gameStart == 'yes'}
	<h3>Quiz has started</h3>
	{#if i === 0}
	<p>{output}</p>
	{/if}
	<p>Choose the plant that best fits the description</p>
	<br>

<!-- determines if the question is a multi-choice or a text input using i (variable created to keep track of question number) -->
	{#if i % 2 == 0}
<!-- if you got the last question wrong, this will say the correct answer, and update you on your total points, unless you are at the first question, where there is then nothing to display from other questions. -->
		{#if i != 0}
			<p>{correction[i-1]}</p>
			<p>{answers[i-1]}</p>
			<br> 
{/if}

<!-- this is the formatting for a multi-choice question -->
		<p>{questionSet[i][1]}</p>
		<label>
						
			<input type=radio bind:group={q1} value={aa}>
			{a}
		</label>

		<label>
			<input type=radio bind:group={q1} value={bb}>
			{b}
		</label>

		<label>
			<input type=radio bind:group={q1} value={cc}>
			{c}
		</label>

		<label>
			<input type=radio bind:group={q1} value={dd}>
			{d}
		</label>

		<button on:click={check(q1)}>
			Check
		</button>

<!-- if your input is invalid, it will print an error message here -->
		<p>{error}</p>

	{:else}
<!-- displays the correction if user got question incorrect, and updates you on score -->
		<p>{correction[i-1]}</p>
		<p>{answers[i-1]}</p>
		<br>

<!-- this is the formatting for the text input variable -->
		<p>{questionSet[i][1]}</p>
		<input type=text bind:value={q2}>
	
		<button on:click={check(q2)}>
			Check
		</button>

<!-- if your input is invalid, it will print an error message here -->
		<p>{error}</p>

	{/if}

<!-- if you have gone through all the questions, then it will go to the final screen, where it shows you your final score, and presents a reset button where you can choose to do the quiz over. -->
{:else if gameStart === 'over'}
	<h3>Quiz Completed</h3>
	<p>{correction[i-1]}</p>
	<p>{finalScore}</p>

	<button id='reset' on:click={reset}>
		Reset
	</button>
{/if}
