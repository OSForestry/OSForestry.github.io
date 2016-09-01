---
layout: page
title: Forestry and GIS Jobs
---
<div id="jobs"></div>


<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js"></script>
<script src="./assets/js/tabletop.js"></script>
<script>
	window.onload = function() { init() };

	function init() {
		Tabletop.init( { 
			key: '1RFdXsCR882hTlI9qRNS0WJuDV-q4LgRQiGPZnPw9hBI',
			callback: fillJobs,
			simpleSheet: true 
		} )
	}

	function showInfo(data, tabletop) {
		alert("Successfully processed!")
		console.log(data);
	}

	function fillJobs(data, tabletop) {
		var today = new Date()
		var htmlString = "";
		for (var i=0,  dataLen=data.length; i < dataLen; i++) {
			console.log(data[i]);
			var deadline = new Date(data[i]['Deadline'])
			if (today < deadline) {
				var htmlString = htmlString.concat("<h2>", data[i]['Title'], "</h2>\n<p>", data[i]['Description'], "</p>\n<a href='", data[i]['Link'], "'>Read More</a>\n<br><br>");
			}
		}
		$('#jobs').html(htmlString);
	}
	
	
</script>