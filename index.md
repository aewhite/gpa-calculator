## GPA Calculator

<textarea id="input" style="width:100%"  placeholder="Enter grades here..."></textarea>

### Results

|:---------------|:------------------------------------------------ |:---------------|:------------------------------------------------ |
| Weighted Count | {::nomarkdown}<div id="weightedCount"></div>{:/} | Count          | {::nomarkdown}<div id="count"></div>{:/}         |
| Weighted Sum   | {::nomarkdown}<div id="weightedSum"></div>{:/}   | Unweighted Sum | {::nomarkdown}<div id="unweightedSum"></div>{:/}           |
| Weighted GPA   | {::nomarkdown}<div id="weightedGpa"></div>{:/}   | Unweighted GPA | {::nomarkdown}<div id="unweightedGpa"></div>{:/} |

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
  var unweightedSum = 0
  var weightedSum = 0
  var count = 0
  var weightedCount = 0
  for (var i = 0; i < input.value.length; i++) {
    let c = input.value.charAt(i)
    if (/\s/.test(c)) { continue }
    if (/[ABCDF]/.test(c)) { weightedCount++ }

    let weightedDelta = gradeValues[c]
    weightedSum += weightedDelta
    let unweightedDelta = gradeValues[c.toLowerCase()]
    unweightedSum += unweightedDelta
    count++
  }

  let weightedGpa = weightedSum/count
  let unweightedGpa = unweightedSum/count
  document.getElementById("unweightedSum").innerHTML = unweightedSum;
  document.getElementById("weightedSum").innerHTML = weightedSum;
  document.getElementById("count").innerHTML = count;
  document.getElementById("weightedCount").innerHTML = weightedCount;
  document.getElementById("weightedGpa").innerHTML = weightedGpa.toFixed(4);
  document.getElementById("unweightedGpa").innerHTML = unweightedGpa.toFixed(4);
})
</script>
