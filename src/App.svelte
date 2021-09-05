<script>
  let q1 = ''
  let q2 = ''
  let q3 = ''
  let q4 = ''
  let q5 = ''
  let currentscore = ''
  let count = 0
  let answers = ['', '', '', '', '']
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
    document.getElementById("button1").style.display = "none";
	}
	
  function check(ans){
		let text = ''
		i++ 
		while (i < 4) {
      if (i === 1) {
        if (ans === 'true') {
          count+= 1 
          text = 'correct!'
        } else {
          text = 'false!' 
        }
			}	else if (i === 2) {
				if (ans === 'carex secta') {
					count+= 1
          text = 'correct!'
        } else {
          text = 'false!' 
        }
			} else if (i === 3) {
				console.log(ans)
				if (ch1.checked & ch3.checked){
					count+= 1 
          text = 'correct!'
        } else {
          text = 'false!'
			} }
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
<p>tussock forming sedge, 1.5-7mm wide light green/yellow-green leaves, up to 1.5m</p>

<input type=text bind:value={q2}>
	
<button id='button2' on:click={check(q2)}>
  Check
</button>

<p>{answers[1]}</p>

<br><br>
<p>Which of these are trees</p>

<label>
	<input id='ch1' type=checkbox bind:group={q3} value={'d'}>
	kowhai
</label>

<label>
	<input id='ch2' type=checkbox bind:group={q3} value={'e'}>
	mahoe
</label>

<label>
	<input id='ch3' type=checkbox bind:group={q3} value={'f'}>
	lancewood
</label>

<label>
	<input id='ch4' type=checkbox bind:group={q3} value={'g'}>
	karamu
</label>

<button id='button3' on:click={check(q3)}>
  Check
</button>

<p>{answers[2]}</p>