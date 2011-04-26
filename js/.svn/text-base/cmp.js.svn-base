function gup( name ){
  name = name.replace(/[\[]/,"\\\[").replace(/[\]]/,"\\\]");
  var regexS = "[\\?&]"+name+"=([^&#]*)";
  var regex = new RegExp( regexS );
  var results = regex.exec( window.location.href );
  if( results == null )
    return "";
  else
    return results[1];
}

function loadSets(){
	$.getJSON("http://api.flickr.com/services/rest/?method=flickr.photosets.getList&api_key=63be78a884a282c64c93648141d8f533&user_id=32554573@N05&format=json&jsoncallback=?", function (data) {
	    var list = $("<ul></ul>");
	    $.each(data.photosets.photoset, function (i, set) {
	        var link = $("<a/>").attr("title", set.description._content)
	            .attr("href", "photos.html?set=" + set.id + "&user=cmponline")
	            .text(set.title._content);
	        var li = $("<li/>").append(link);
	        $(list).append(li);
	    });
	    $("#photo-sets").append(list);
	});
}

function loadFlickr(){
	var set_param = gup( 'set' );
	var user_param = gup( 'user' );
	if (set_param != ""){
		$('a.media').media({ 
	    	flashvars: { 
		        offsite: 'true', 
		        lang: 'en-us',
		        page_show_url: '%2Fphotos%2F' + user_param + '%2Fsets%2F'+ set_param + '%2Fshow%2F', 
		        page_show_back_url: '%2Fphotos%2F' + user_param + '%2Fsets%2F' + set_param + '%2F&set_id='+ set_param 
		    },
			params: { 
		        allowFullScreen: 'true'	        
		    },
			type:'swf',
			width:'400',
			height:'300'
		});
		$('#select-text').hide();
	}
}

function loadServicesNav()
{
	$("#sidemenu").load("includes/services.html");	      
}

$(document).ready(function(){
  	$("#footer-wrapper").load("includes/footer.html");	      
});

