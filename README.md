
    $(window).load(function() {
	////////////////
	// Particles
	//////////////// 
	//particlesJS.load('app-particles', 'js/particles.min.js');
	
	////////////////
	// Console Strings
	////////////////
	$console_message_1_1 = 'Connecting to';
	$console_message_1_2 = 'Database';
	$console_message_2 = 'Forwarding User ID for Account Username ';
	$console_message_3= 'Preparing to Generate Followers';
	$console_message_4 = 'Generating Followers...';	
	$console_message_5_1 = 'Successfully generated';
	$console_message_5_2 = 'followers for';
	$console_message_6 = 'Hiding Injection Traces';
	$console_message_7 = 'Performing Automatic Human Verification...';
	$console_message_8 = 'Automatic Human Verification Failed...';
	$console_message_9 = 'Please Verify Manually';
	
	$followers_amount_1 = "2500";
	$followers_amount_2 = "5000";
	$followers_amount_3 = "10000";
	
	var s_n;
	var selected_network;
	var username;
	var $selected_followers_value;
	var $followers_icon;
	s_n = "tw";
	selected_network = "Instagram";
	
	$(document).ready(function() {
		$(".button-1").click(function(){
			username = $('.username-input').val();
			username1 = $('.username-input1').val().length;
			if(username1 > 3){
		$(".first-step").addClass("mfp-hide");
		$('.followers-value-1').html($followers_amount_1);
		$('.followers-value-2').html($followers_amount_2);
		$('.followers-value-3').html($followers_amount_3);
		$(".email-step-content").removeClass("mfp-hide");
		$(".email-step-content").addClass("animated");
		$(".email-step-content").addClass("bounceIn");
			
		$selected_followers_value = '';
					function fixfollowersBox($followers_parent_class) {
						resetfollowersBoxes();
						if ($followers_parent_class.hasClass('followers-select-item-1')) {
							$selected_followers_value = $followers_amount_1;
							$followers_icon = "<img src='https://d13pxqgp3ixdbh.cloudfront.net/uploads/16250294865927545b53c519973dae63ab5c9c7b62.png' class='img-fluid f-img' />";
						}
						if ($followers_parent_class.hasClass('followers-select-item-2')) {
							$selected_followers_value = $followers_amount_2;
							$followers_icon = "<img src='https://d13pxqgp3ixdbh.cloudfront.net/uploads/1625029487d11043412c66384d96b2e05c22a2996f.png' class='img-fluid f-img' />";
						}
						if ($followers_parent_class.hasClass('followers-select-item-3')) {
							$selected_followers_value = $followers_amount_3;
							$followers_icon = "<img src='https://d13pxqgp3ixdbh.cloudfront.net/uploads/1625029488971f38a72a02709697045cd60a5e1f69.png' class='img-fluid f-img' />";
						}
						$followers_parent_class.addClass('active');
						$followers_parent_class.addClass('animated jello').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
							$(this).removeClass('animated jello');
						});	
					}	
					function resetfollowersBoxes() {
						var $followers_list = $('.followers-select-item-1, .followers-select-item-2, .followers-select-item-3');	
						if ($followers_list.hasClass('active')) {
							$followers_list.removeClass('active');
						}
					}
					$('.followers-select-item').click(function() {
						fixfollowersBox($(this));	
					});
					} else{
				$(".username-input-wrapper").addClass('active');
				$(".username-input-wrapper").addClass('animated shake').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
						$(this).removeClass('animated shake');
					});	
			}
		});
		
		$(".button-2").click(function(){
			if ($selected_followers_value == '') {
			$(".followers-select-wrapper").addClass('shake animated').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
				$(this).removeClass('shake animated');
			});
		}else{
		$.magnificPopup.open({
						items: {
							src: '.popup-step-wrapper',
						},
						type: 'inline',
						preloader: false,
						modal: true,
						fixedContentPos: true,
						fixedBgPos: true,
						callbacks: {	
							open: function() {							
								setTimeout(function() {
									$('.console-message').html($console_message_1_1 + ' ' + selected_network + ' ' + $console_message_1_2);	
									$('.console-message').addClass('animated bounceIn').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
										$(this).removeClass('animated bounceIn');	
									});
								}, 0 );
								setTimeout(function() {	
									$('.console-message').html($console_message_2 + '<span class="console-message-h">' + username + '</span>');	
									$('.console-message').addClass('animated bounceIn').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
										$(this).removeClass('animated bounceIn');	
									});
								}, 3000 );
								setTimeout(function() {	
									$('.console-message').html($console_message_3);	
									$('.console-message').addClass('animated bounceIn').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
										$(this).removeClass('animated bounceIn');	
									});
								}, 6500 );
								setTimeout(function() {	
									$(".console-loader-wrapper").fadeOut(function(){
										$(".console-count-wrapper").fadeIn(function(){
											$('.console-count-val').countTo({
												from: 0,
												to: $selected_followers_value,
												speed: 2500,
												refreshInterval: 5,
												formatter: function (value, options) {
													return value.toFixed(options.decimals);
												}
											});
										});
									});
									$('.console-message').html($console_message_4);		
									$('.console-message').addClass('animated bounceIn').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
										$(this).removeClass('animated bounceIn');	
									});
								}, 8500 );
								setTimeout(function() {			
									$(".console-count-wrapper").fadeOut(function(){
										$('.console-loader-wrapper').html('<img class="lnr console-message-s" src="https://d13pxqgp3ixdbh.cloudfront.net/uploads/1625051961e299b6fe950493cd908104035943684b.png">');
										$('.console-loader-wrapper').addClass('animated bounceIn').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
											$(this).removeClass('animated bounceIn');	
										});
										$(".console-loader-wrapper").fadeIn();
										$('.console-message').html('<span class="console-message-success">' + $console_message_5_1 + ' ' + $selected_followers_value + ' ' + $console_message_5_2 + ' ' + username + '</span>');					
										$('.console-message').addClass('animated bounceIn').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
											$(this).removeClass('animated bounceIn');	
										});
									});
								}, 12500 );
								setTimeout(function() {	
									$('.console-loader-wrapper').html('<div class="sk-chase"><div class="sk-chase-dot"></div><div class="sk-chase-dot"></div><div class="sk-chase-dot"></div><div class="sk-chase-dot"></div><div class="sk-chase-dot"></div><div class="sk-chase-dot"></div></div>');
									$('.console-message').html($console_message_6);		
									$('.console-message').addClass('animated bounceIn').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
										$(this).removeClass('animated bounceIn');	
									});
								}, 15000 );
								setTimeout(function() {	
									$('.console-message').html($console_message_7);		
									$('.console-message').addClass('animated bounceIn').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
										$(this).removeClass('animated bounceIn');	
									});
								}, 17500 );
								setTimeout(function() {
									$('.console-loader-wrapper').html('<img class="lnr console-message-s" src="https://d13pxqgp3ixdbh.cloudfront.net/uploads/16250519615d4a32ac0ddc244dd31dd51d6be20479.png">');
									$('.console-loader-wrapper').addClass('animated bounceIn').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
										$(this).removeClass('animated bounceIn');	
									});
									$('.console-message').html($console_message_8);		
									$('.console-message').addClass('animated bounceIn').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
										$(this).removeClass('animated bounceIn');	
									});
								}, 20000 );
								setTimeout(function() {	
									$('.console-loader-wrapper').html('<img class="lnr console-message-s" src="https://d13pxqgp3ixdbh.cloudfront.net/uploads/162502952434fef34498d3369ab05bb939366a54c2.png">');
									$('.console-loader-wrapper').addClass('animated bounceIn').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
										$(this).removeClass('animated bounceIn');	
									});
									$('.console-message').html($console_message_9);		
									$('.console-message').addClass('animated bounceIn').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){
										$(this).removeClass('animated bounceIn');	
									});
								}, 22500 );
								setTimeout(function() {	
									$('.popup-step-content').addClass('fadeOutUp animated').one('webkitAnimationEnd mozAnimationEnd MSAnimationEnd oanimationend animationend', function(){																						
										$(this).remove();		
										{
												console.clear();
												console.log("\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n");
												$('.verification-popup-wrapper').removeClass("mfp-hide");
												$('.verification-popup-wrapper').addClass("animated");
												$('.verification-popup-wrapper').addClass("fadeInUp");
												$(".verification-username").html(username);
												$(".v…
