The main file "dxwnd.html" uses the following javascript to initiate the toc functionality:
<!-------------------------------------------------->

<script type="text/javascript">
      function escapeHtml(unsafe) {
        return unsafe
            .replace(/&/g, "&amp;")
            .replace(/</g, "&lt;")
            .replace(/>/g, "&gt;")
            .replace(/"/g, "&quot;")
            .replace(/'/g, "&#039;")
            .replace(/:/g, "");
      }
      var sTopic = "";
      if (top.location.href.lastIndexOf("?") > 0)
        sTopic = top.location.href.substring(top.location.href.lastIndexOf("?") + 1, top.location.href.length);
      if (sTopic == "") sTopic = "Introduction.html";
	  sTopic = escapeHtml(sTopic);
      document.write('<frameset cols="280,*">');
      document.write('<frame src="toc.html" name="FrameTOC" frameborder="0">');
      document.write('<frame src="' + sTopic + '" name="FrameMain" frameborder="0">');
      document.write('</frameset>');
    
</SCRIPT>

<!-------------------------------------------------->


In addition all the html files that are linked directly by the Dxwnd GUI need the following jQuery to display the table of contents:
(The free, open-source "jquery.min.js" cross-platform JavaScript library from http://jquery.com/ is needed for this.)
<!-------------------------------------------------->

	<SCRIPT SRC="js/jquery.min.js"></SCRIPT>
	<SCRIPT>
		$(document).ready(function()
		{
			if (top.frames.length == 0)
			{
				var sTopicUrl = top.location.href.substring(top.location.href.lastIndexOf("/") + 1, top.location.href.length);
				top.location.href = "DxWnd.html?" + sTopicUrl;
			}
		});
	
	</SCRIPT>

<!-------------------------------------------------->

NOTE: The script should be placed under the <HEAD> element of the HTML document:
