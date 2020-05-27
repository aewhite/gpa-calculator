## GPA Calculator

<textarea id="input" style="width:100%"  placeholder="Enter grades here..."></textarea>

### Results

<div class="table-wrapper" style="width:25%" markdown="block">
	
|:---------|:---------------------------------------------|
| Sum      | {::nomarkdown}<div id="sum"></div>{:/}       |
| Count    | {::nomarkdown}<div id="count"></div>{:/}     |
| Weighted | {::nomarkdown}<div id="weighted"></div>{:/}  |
| GPA      | {::nomarkdown}<div id="gpa"></div>{:/}       |

</div>

<script>
const gradeValues = {
        'a': 4,
        'b': 3,
        'c': 2,
        'd': 1,
        'f': 0,
        'A': 5,
        'B': 4,
        'C': 3,
        'D': 2,
        'F': 0,
        }
let input = document.getElementById("input"); 
input.addEventListener("input", function() {
	var sum = 0
  var count = 0
  var weighted = 0
  for (var i = 0; i < input.value.length; i++) {
  	let c = input.value.charAt(i)
    if (/\s/.test(c)) { continue }
    if (/[ABCDF]/.test(c)) { weighted++ }
		let delta = gradeValues[c]
    sum += delta
    count++
	}
  
  let gpa = sum/count
	document.getElementById("sum").innerHTML = sum;
	document.getElementById("count").innerHTML = count;
	document.getElementById("weighted").innerHTML = weighted;
  document.getElementById("gpa").innerHTML = gpa.toFixed(2);
})
</script>
