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

	.sk-folding-cube {
		margin: 20px auto;
		width: 40px;
		height: 40px;
		position: relative;
		-webkit-transform: rotateZ(45deg);
						transform: rotateZ(45deg);
	}

	.sk-folding-cube .sk-cube {
		float: left;
		width: 50%;
		height: 50%;
		position: relative;
		-webkit-transform: scale(1.1);
				-ms-transform: scale(1.1);
						transform: scale(1.1); 
	}
	.sk-folding-cube .sk-cube:before {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: #333;
		-webkit-animation: sk-foldCubeAngle 2.4s infinite linear both;
						animation: sk-foldCubeAngle 2.4s infinite linear both;
		-webkit-transform-origin: 100% 100%;
				-ms-transform-origin: 100% 100%;
						transform-origin: 100% 100%;
	}
	.sk-folding-cube .sk-cube2 {
		-webkit-transform: scale(1.1) rotateZ(90deg);
						transform: scale(1.1) rotateZ(90deg);
	}
	.sk-folding-cube .sk-cube3 {
		-webkit-transform: scale(1.1) rotateZ(180deg);
						transform: scale(1.1) rotateZ(180deg);
	}
	.sk-folding-cube .sk-cube4 {
		-webkit-transform: scale(1.1) rotateZ(270deg);
						transform: scale(1.1) rotateZ(270deg);
	}
	.sk-folding-cube .sk-cube2:before {
		-webkit-animation-delay: 0.3s;
						animation-delay: 0.3s;
	}
	.sk-folding-cube .sk-cube3:before {
		-webkit-animation-delay: 0.6s;
						animation-delay: 0.6s; 
	}
	.sk-folding-cube .sk-cube4:before {
		-webkit-animation-delay: 0.9s;
						animation-delay: 0.9s;
	}
	@-webkit-keyframes sk-foldCubeAngle {
		0%, 10% {
			-webkit-transform: perspective(140px) rotateX(-180deg);
							transform: perspective(140px) rotateX(-180deg);
			opacity: 0; 
		} 25%, 75% {
			-webkit-transform: perspective(140px) rotateX(0deg);
							transform: perspective(140px) rotateX(0deg);
			opacity: 1; 
		} 90%, 100% {
			-webkit-transform: perspective(140px) rotateY(180deg);
							transform: perspective(140px) rotateY(180deg);
			opacity: 0; 
		} 
	}

	@keyframes sk-foldCubeAngle {
		0%, 10% {
			-webkit-transform: perspective(140px) rotateX(-180deg);
							transform: perspective(140px) rotateX(-180deg);
			opacity: 0; 
		} 25%, 75% {
			-webkit-transform: perspective(140px) rotateX(0deg);
							transform: perspective(140px) rotateX(0deg);
			opacity: 1; 
		} 90%, 100% {
			-webkit-transform: perspective(140px) rotateY(180deg);
							transform: perspective(140px) rotateY(180deg);
			opacity: 0; 
		}
	}
</style>

<div id="jobs"></div>

<div class="sk-folding-cube">
  <div class="sk-cube1 sk-cube"></div>
  <div class="sk-cube2 sk-cube"></div>
  <div class="sk-cube4 sk-cube"></div>
  <div class="sk-cube3 sk-cube"></div>
</div>

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
		var htmlString = htmlString.concat('<p style="text-align: center;"><a style="color: black;" target="_blank" href="https://docs.google.com/forms/d/1X9gOcBp9A7k04w6Av1MdorOB2PYWielpnb4vgbdi8X0/">Submit a Position</a></p>');
		$('.sk-folding-cube').css('display', 'none')
		$('#jobs').html(htmlString);
	}
	
	
</script>