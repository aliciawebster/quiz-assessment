<script>
	let q1 = ''
  let q2 = ''
  let q3 = ''
  let q4 = ''
  let q5 = ''
	let q6 = ''
  let q7 = ''
  let q8 = ''
  let q9 = ''
  let q10 = ''
	let currentscore = ''
  let count = 0
  let answers = ['', '', '', '', '', '', '', '', '', '']
	let correction = ['', '', '', '', '', '', '', '', '', '']
  let i = 0
  let finalscore = ''
	let name = ''
  let group = ''
	let length = ''
	let questionSet = ''
	let p = ''
	let gameStart = 'no'		
	let q = ''
	let a = ''
	let b = ''
	let c = ''
	let d = ''

  
  let questions = [
  ['kowhai', 'yellow flowers in spring, small leaflets, can grow up to 25m', '../src/assets/images/kowhai.jpg'],
  ['kahikatea', 'conifer (cone bearing) tree, can grow over 50m', '../src/assets/images/kahikatea.jpg'],
  ['poroporo', 'fleshy shrub, yellow/orange fruits, purple ruffled flowers, up to 4m', '../src/assets/images/poroporo.jpg'],
  ['mingimingi', 'divaricating shrub, small oblong leaves, translucent blue berries', '../src/assets/images/mingimingi.jpg'],
  ['karamu', 'large bushy shrub, red fruits in tight clusters along twigs, grows to 4m', '../src/assets/images/karamu.jpg'],
  ['lancewood', 'thin straight trunk, lance-like foliage, drooping spiky leaves, up to 15m', '../src/assets/images/lancewood.jpg'],
  ['akeake', 'bushy shrub/small tree, reddish bark, long thin wavy leaves, greenish white flowers with yellow or red tips, up to 12m', '../src/assets/images/akeake.jpg'],
  ['cabbage tree', 'long narrow leaves up to 1m, white flowers turn to bluish-white berries, height up to 20m', '../src/assets/images/cabbagetree.jpg'],
  ['carex secta', 'tussock forming sedge, 1.5-7mm wide light green/yellow-green leaves, up to 1.5m', '../src/assets/images/carexsecta.jpg'],
  ['mahoe', 'shrub or small tree, greenish flowers in clusters along twigs, purple fruit, up to 15m', '../src/assets/images/mahoe.jpg']
  ]
	
	function reset() {
    count = 0
    i = 0
		name = ''
 	  group = ''
		length = ''
		gameStart = 'no'
		p = ''
		answers = ['', '', '', '', '', '', '', '', '', '']
		correction = ['', '', '', '', '', '', '', '', '', '']
  	}
	
	function start(n, g, le){
		if (g === '') {
				p = 'please enter your form class '
				if  (n === '') {
					p += 'and name '} 
				if  (le < 3 || le > 20) {
					p += 'and a number between 3 and 20' }
		} else if  (n === '') {
			p = 'please enter your name '
			if  (le < 3 || le > 20) {
					p += 'and a number between 3 and 20' }
		} else if  (le < 3 || le > 20) {
			p = 'please choose a number between 3 and 20'
		} else {
		p = 'Hello ' + n + ' from class ' + g
		gameStart = 'yes'
		shuffle(le)
		}
		return p
	}
	
	function shuffle(l){
		// shuffle questions
		var m = questions.length, t, i;
		// This checks there are still questions to shuffle
		while (m) {
			// Picks a remaining element randomly
			i = Math.floor(Math.random() * m--);
			// This swaps that with the current element
			t = questions[m];
			questions[m] = questions[i];
			questions[i] = t;
		}
		questionSet = questions.slice()
		questionSet.splice(l, 10-l)
		return questionSet
	} 
	
  function check(ans){
		let text = '' 
		while (i < length) {
      if (i % 2 == 0) {
        if (ans === 'true') {
          count+= 1 
          text = 'correct!'
        } else {
          text = 'false!' 
					correction[i] = 'correct answer was ' + questionSet[i][0]

        }
			}	else if (i % 2 != 0) {
				if (ans === questionSet[i][0]) {
					count+= 1
          text = 'correct!'
        } else {
          text = 'false!' 
					correction[i] = 'correct answer was ' + questionSet[i][0]
        } 
			} 
			i++
			text += ' current score is ' + count
    	answers[i-1] = text
			q = ''
			if (i === length) {
				finalscore = 'Your final score is ' + count + '!'
				gameStart = 'over'
				console.log(gameStart)
			}
			return answers
		} 
	}

	function multi() {
		let num = Math.floor(Math.random() * 5);
		if (num === 1) {
			a = questionSet[i][0]
			b = questions[Math.floor(Math.random() * 10)][0]
			

		} else if (num === 2) {
			b = questionSet[i][0]
			
		} else if (num === 3) {
			c = questionSet[i][0]
			
		} else {
			d = questionSet[i][0]

		}
	}
	
</script>

{#if (gameStart == 'no')}
	<h3>Native Plants Quiz</h3>
	<p>Identifing Native Plants</p>
	<br>

	<p>Enter your name and tutor group, and choose a quiz length from three to twenty.</p>

	<input type=text bind:value={name} placeholder='enter name'>
	<input type=text bind:value={group} placeholder='enter tutor group'>
	<input type=number bind:value={length} placeholder='quiz length'>
	
	<button on:click={start(name, group, length, gameStart)}>
		Go
	</button>
	<p>{p}</p>

{:else if gameStart == 'yes'}
	<h3>Quiz has started</h3>
	<p>Choose the plant that best fits the description</p>
	<br>

	{#if i % 2 == 0}
		{#if i != 0}
			<p>{correction[i-1]}</p>
			<p>{answers[i-1]}</p>
			<br> 
{/if}

		<p>{questionSet[i][1]}</p>
		<label>
						
			<input type=radio bind:group={q} value={a}>
			{questions[2][0]}
		</label>

		<label>
			<input type=radio bind:group={q} value={'b'}>
			{questions[3][0]}
		</label>

		<label>
			<input type=radio bind:group={q} value={'true'}>
			{questionSet[i][0]}
		</label>

		<label>
			<input type=radio bind:group={q} value={'c'}>
			{questions[7][0]}
		</label>

		<button on:click={check(q)}>
			Check
		</button>

	{:else}
		<p>{correction[i-1]}</p>
		<p>{answers[i-1]}</p>
		<br>

		<p>{questionSet[i][1]}</p>
		<input type=text bind:value={q}>
	
		<button on:click={check(q)}>
			Check
		</button>

	{/if}

{:else if gameStart === 'over'}
	<h3>Quiz Completed</h3>
	<p>{correction[i-1]}</p>
	<p>{finalscore}</p>

	<button id='reset' on:click={reset}>
		Reset
	</button>
{/if}

