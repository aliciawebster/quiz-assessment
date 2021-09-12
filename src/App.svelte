<script>
  let name = ''
  let group = ''
	let length = ''
  let currentscore = ''
  let count = 0
  let answers = ['', '', '', '', '', '', '', '', '', '']
  let qnum = 0
  let finalscore = ''
	let p = ''
  
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
	
	function start(n, g, l){
		if (g === '') {
				p = 'please enter your form class '
				if  (n === '') {
					p += 'and name '} 
				if  (l < 3 || l > 20) {
					p += 'and a number between 3 and 30' }
		} else if  (n === '') {
			p = 'please enter your name '
			if  (l < 3 || l > 20) {
					p += 'and a number between 3 and 30' }
		} else if  (l < 3 || l > 20) {
			p = 'please choose a number between 3 and 30'
		} else {
		p = 'Hello ' + n + ' from class ' + g
		shuffle(l)
		}
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
	} 
	
</script>

<h3>Native Plants Quiz</h3>
<p>Identifing Native Plants</p>
<br>

<p>Enter your name and tutor group, and choose a quiz length from three to twenty.</p>

<input type=text bind:value={name} placeholder='enter name'>
<input type=text bind:value={group} placeholder='enter tutor group'>
<input type=number bind:value={length} placeholder='quiz length'>

<button on:click={start(name, group, length)}>
  Go
</button>


<p>{p}</p>
