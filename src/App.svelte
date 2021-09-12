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
  let qnum = 0
  let finalscore = ''
	let name = ''
  let group = ''
	let length = ''
	let questionSet = ''
	let p = ''
	let gameStart = false		
  
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
	
	function start(n, g, le){
		if (g === '') {
				p = 'please enter your form class '
				if  (n === '') {
					p += 'and name '} 
				if  (le < 3 || le > 20) {
					p += 'and a number between 3 and 30' }
		} else if  (n === '') {
			p = 'please enter your name '
			if  (le < 3 || le > 20) {
					p += 'and a number between 3 and 30' }
		} else if  (le < 3 || le > 20) {
			p = 'please choose a number between 3 and 30'
		} else {
		p = 'Hello ' + n + ' from class ' + g
		gameStart = true
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
		i++ 
		while (i < 11) {
			console.log(ans)
			document.getElementById("button" + i).style.display = "none";
      if (i === 1 || i === 3 || i === 5 || i === 7) {
        if (ans === 'true') {
          count+= 1 
          text = 'correct!'
        } else {
          text = 'false!' 
					correction[i-1] = 'correct answer was ' + questionSet[i][0]
        }
			}	else if (i === 2 || i === 4 || i === 6 || i === 8) {
				if (ans === questionSet[i][0]) {
					count+= 1
          text = 'correct!'
        } else {
          text = 'false!' 
					correction[i-1] = 'correct answer was ' + questionSet[i][0]
        } 
			}
			text += ' current score is ' + count
    	answers[i-1] = text
			return answers 
		} 
	}

</script>

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

{#if (gameStart == true)}
	<br>
	<h4>Quiz has started</h4>
	<p>Choose the plant that best fits the description</p>
	<br>

<br>
<p>{questionSet[1][1]}</p>
<label>
	<input type=radio bind:group={q1} value={'a'}>
	{questions[2][0]}
</label>

<label>
	<input type=radio bind:group={q1} value={'b'}>
	{questions[0][0]}
</label>

<label>
	<input type=radio bind:group={q1} value={'true'}>
	{questionSet[1][0]}
</label>

<label>
	<input type=radio bind:group={q1} value={'c'}>
	{questions[7][0]}
</label>

<button id='button1' on:click={check(q1)}>
  Check
</button>

<p>{correction[0]}</p>
<p>{answers[0]}</p>

<br>
<p>{questionSet[2][1]}</p>

<input type=text bind:value={q2}>
	
<button id='button2' on:click={check(q2)}>
  Check
</button>

<p>{answers[1]}</p>
<p>{correction[1]}</p>

<br>
<p>{questionSet[3][1]}</p>

<label>
	<input type=radio bind:group={q3} value={'h'}>
	{questions[4][0]}
</label>

<label>
	<input type=radio bind:group={q3} value={'true'}>
	{questionSet[3][0]}
</label>

<label>
	<input type=radio bind:group={q3} value={'i'}>
	{questions[9][0]}
</label>

<label>
	<input type=radio bind:group={q3} value={'j'}>
	{questions[1][0]}
</label>

<button id='button3' on:click={check(q3)}>
  Check
</button>

<p>{answers[2]}</p>
<p>{correction[2]}</p>

<br>
<p>{questionSet[4][1]}</p>

<input type=text bind:value={q4}>
	
<button id='button4' on:click={check(q4)}>
  Check
</button>

<p>{answers[3]}</p>
<p>{correction[3]}</p>

<br>
<p>{questionSet[5][1]}</p>
<label>
	<input type=radio bind:group={q5} value={'o'}>
	{questions[8][0]}
</label>

<label>
	<input type=radio bind:group={q5} value={'p'}>
	{questions[6][0]}
</label>

<label>
	<input type=radio bind:group={q5} value={'q'}>
	{questions[5][0]}
</label>

<label>
	<input type=radio bind:group={q5} value={'true'}>
	{questionSet[5][0]}
</label>

<button id='button5' on:click={check(q5)}>
  Check
</button>

<p>{answers[4]}</p>
<p>{correction[4]}</p>

<br>
<p>{questionSet[6][1]}</p>

<input type=text bind:value={q6}>
	
<button id='button6' on:click={check(q6)}>
  Check
</button>

<p>{answers[5]}</p>
<p>{correction[5]}</p>

<br>
<p>{questionSet[7][1]}</p>
<label>
	<input type=radio bind:group={q7} value={'true'}>
	{questions[7][0]}
</label>

<label>
	<input type=radio bind:group={q7} value={'r'}>
	{questions[1][0]}
</label>

<label>
	<input type=radio bind:group={q7} value={'s'}>
	{questions[9][0]}
</label>

<label>
	<input type=radio bind:group={q7} value={'u'}>
	{questions[8][0]}
</label>

<button id='button7' on:click={check(q7)}>
  Check
</button>

<p>{answers[6]}</p>
<p>{correction[6]}</p>

<br>
<p>{questionSet[8][1]}</p>

<input type=text bind:value={q8}>
	
<button id='button8' on:click={check(q8)}>
  Check
</button>

<p>{answers[7]}</p>
<p>{correction[7]}</p>

<br>
{/if}