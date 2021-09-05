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
  let i = 0
  let qnum = 0
  let finalscore = ''
  
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
	
	function update(t) {
		t += ' current score is ' + count
    answers[i-1] = t
	}
	
  function check(ans){
		let text = ''
		i++ 
		while (i < 11) {
      if (i === 1) {
				document.getElementById("button1").style.display = "none";
        if (ans === 'true') {
          count+= 1 
          text = 'correct!'
        } else {
          text = 'false!' 
        }
			}	else if (i === 2) {
				document.getElementById("button2").style.display = "none";
				if (ans === 'carex secta') {
					count+= 1
          text = 'correct!'
        } else {
          text = 'false!' 
        }
			} else if (i === 3) {
				document.getElementById("button3").style.display = "none";
				if (ch1.checked & ch3.checked){
					count+= 1 
          text = 'correct!'
        } else {
          text = 'false!'
				}
			} else if (i === 4) {
				document.getElementById("button4").style.display = "none";
					if (ans === 'true') {
						count+= 1
						text = 'correct!'
					} else {
						text = 'false!' 
					}
			} else if (i === 5) {
				document.getElementById("button5").style.display = "none";
				if (ans === 'mingimingi') {
					count+= 1
          text = 'correct!'
        } else {
          text = 'false!' 
        }
			} else if (i === 6) {
				document.getElementById("button6").style.display = "none";
				if (ch5.checked & ch6.checked){
					count+= 1 
          text = 'correct!'
        } else {
          text = 'false!'
				}
			} else if (i === 7) {
				document.getElementById("button7").style.display = "none";
					if (ans === 'true') {
						count+= 1
						text = 'correct!'
					} else {
						text = 'false!' 
					}
			} else if (i === 8) {
				document.getElementById("button8").style.display = "none";
				if (ans === 'akeake') {
					count+= 1
          text = 'correct!'
        } else {
          text = 'false!' 
        }
			} else if (i === 9) {
				document.getElementById("button9").style.display = "none";
					if (ans === 'true') {
						count+= 1
						text = 'correct!'
					} else {
						text = 'false!' 
					}
			} else if (i === 10) {
				document.getElementById("button10").style.display = "none";
				if (ans === 'lancewood') {
					count+= 1
          text = 'correct!'
        } else {
          text = 'false!' 
        }
			}
			update(text)
			return answers 
		} 
	}

</script>


<h3>Native Plants Quiz</h3>
<p>Identifing Native Plants</p>

<br>
<p>{questions[1][1]}</p>
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
	{questions[1][0]}
</label>

<label>
	<input type=radio bind:group={q1} value={'c'}>
	{questions[7][0]}
</label>

<button id='button1' on:click={check(q1)}>
  Check
</button>

<p>{answers[0]}</p>

<br>
<p>{questions[8][1]}</p>

<input type=text bind:value={q2}>
	
<button id='button2' on:click={check(q2)}>
  Check
</button>

<p>{answers[1]}</p>

<br>
<p>Which of these are trees</p>

<label>
	<input id='ch1' type=checkbox bind:group={q3} value={'d'}>
	{questions[0][0]}
</label>

<label>
	<input id='ch2' type=checkbox bind:group={q3} value={'e'}>
	{questions[9][0]}
</label>

<label>
	<input id='ch3' type=checkbox bind:group={q3} value={'f'}>
	{questions[5][0]}
</label>

<label>
	<input id='ch4' type=checkbox bind:group={q3} value={'g'}>
	{questions[4][0]}
</label>

<button id='button3' on:click={check(q3)}>
  Check
</button>

<p>{answers[2]}</p>

<br>
<p>{questions[6][1]}</p>

<label>
	<input type=radio bind:group={q4} value={'h'}>
	{questions[4][0]}
</label>

<label>
	<input type=radio bind:group={q4} value={'true'}>
	{questions[6][0]}
</label>

<label>
	<input type=radio bind:group={q4} value={'i'}>
	{questions[9][0]}
</label>

<label>
	<input type=radio bind:group={q4} value={'j'}>
	{questions[1][0]}
</label>

<button id='button4' on:click={check(q4)}>
  Check
</button>

<p>{answers[3]}</p>

<br>
<p>{questions[3][1]}</p>

<input type=text bind:value={q5}>
	
<button id='button5' on:click={check(q5)}>
  Check
</button>

<p>{answers[4]}</p>

<br>
<p>which of these produce berries/fruits?</p>

<label>
	<input id='ch5' type=checkbox bind:group={q6} value={'k'}>
	{questions[4][0]}
</label>

<label>
	<input id='ch6' type=checkbox bind:group={q6} value={'l'}>
	{questions[9][0]}
</label>

<label>
	<input id='ch7' type=checkbox bind:group={q6} value={'m'}>
	{questions[1][0]}
</label>

<label>
	<input id='ch8' type=checkbox bind:group={q6} value={'n'}>
	{questions[2][0]}
</label>

<button id='button6' on:click={check(q6)}>
  Check
</button>

<p>{answers[5]}</p>

<br>
<p>{questions[7][1]}</p>
<label>
	<input type=radio bind:group={q7} value={'o'}>
	{questions[8][0]}
</label>

<label>
	<input type=radio bind:group={q7} value={'p'}>
	{questions[6][0]}
</label>

<label>
	<input type=radio bind:group={q7} value={'q'}>
	{questions[5][0]}
</label>

<label>
	<input type=radio bind:group={q7} value={'true'}>
	{questions[7][0]}
</label>

<button id='button7' on:click={check(q7)}>
  Check
</button>

<p>{answers[6]}</p>

<br>
<p>{questions[6][1]}</p>

<input type=text bind:value={q8}>
	
<button id='button8' on:click={check(q8)}>
  Check
</button>

<p>{answers[7]}</p>

<br>
<p>{questions[4][1]}</p>
<label>
	<input type=radio bind:group={q9} value={'true'}>
	{questions[4][0]}
</label>

<label>
	<input type=radio bind:group={q9} value={'r'}>
	{questions[1][0]}
</label>

<label>
	<input type=radio bind:group={q9} value={'s'}>
	{questions[9][0]}
</label>

<label>
	<input type=radio bind:group={q9} value={'u'}>
	{questions[8][0]}
</label>

<button id='button9' on:click={check(q9)}>
  Check
</button>

<p>{answers[8]}</p>

<br>
<p>{questions[5][1]}</p>

<input type=text bind:value={q10}>
	
<button id='button10' on:click={check(q10)}>
  Check
</button>

<p>{answers[9]}</p>

<br>