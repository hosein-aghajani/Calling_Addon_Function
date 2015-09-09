// privileged scope: for example, a content script (i.e. a firefox addon)

function changeMyName(user) {
  user.name = "Bill";
}

exportFunction(changeMyName, contentWindow, {
  defineAs: "changeMyName"
});



// less-privileged scope: for example, a page script (i.e. a jsp)

var user = {name: "Jim"};

var test = document.getElementById("test");
test.addEventListener("click", function() {
  console.log(user.name);            // "Jim"
  window.changeMyName(user);
  console.log(user.name);            // "Bill"
}, false);
