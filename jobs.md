---
layout: page
title: Forestry and GIS Jobs
---
<style>
	.job-title {
		float: left;
	}
	.pay-rate {
		text-align: right;
		line-height: 3;
		font-weight: 400;
	}
	.job-meta {
		width: 100%;
		margin-bottom: 15px;
	}
	.job-meta td {
		padding: 0;
		font-style: italic;
	}
	.job-meta td:last-child {
		text-align: right;
	}
</style>

<div id="jobs"></div>
<p style="text-align: center;"><a style="color: black;" target="_blank" href="https://docs.google.com/forms/d/1X9gOcBp9A7k04w6Av1MdorOB2PYWielpnb4vgbdi8X0/edit?usp=sharing">Submit a Position</a></p>


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
				var htmlString = htmlString.concat('\
					<h2 class="job-title">', data[i]['Title'], '</h2><p class="pay-rate">', data[i]['Pay Rate'], '</p>\n\
					<table class="job-meta">\n\
						<tr>\n\
							<td class="employer">', data[i]['Employer'], '</td>\n\
							<td class="posted">Posted: ', data[i]['Posted'], '</td>\n\
						</tr>\n\
						<tr>\n\
							<td class="location">', data[i]['Location'], '</td>\n\
							<td class="posted">Deadline: ', data[i]['Deadline'], '</td>\n\
						</tr>\n\
					</table>\n\
					<p class="description">', data[i]['Description'], '</p>\n\
					<a class="read-more" target="_blank" href="', data[i]['Link'], '">Read more</a>\n\
					<br><br><br><br>\n\
					');
			}
		}
		$('#jobs').html(htmlString);
	}
	
	
</script>