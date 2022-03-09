<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/xhtml;charset=UTF-8"/>
<meta http-equiv="X-UA-Compatible" content="IE=9"/>
<meta name="generator" content="Doxygen 1.8.15"/>
<meta name="viewport" content="width=device-width, initial-scale=1"/>
<title>OSML(Open sharp media library): Osml (Open sharp media library) project</title>
<link href="tabs.css" rel="stylesheet" type="text/css"/>
<script type="text/javascript" src="jquery.js"></script>
<script type="text/javascript" src="dynsections.js"></script>
<link href="search/search.css" rel="stylesheet" type="text/css"/>
<script type="text/javascript" src="search/searchdata.js"></script>
<script type="text/javascript" src="search/search.js"></script>
<link href="doxygen.css" rel="stylesheet" type="text/css" />
</head>
<body>
<div id="top"><!-- do not remove this div, it is closed by doxygen! -->
<div id="titlearea">
<table cellspacing="0" cellpadding="0">
 <tbody>
 <tr style="height: 56px;">
  <td id="projectalign" style="padding-left: 0.5em;">
   <div id="projectname">OSML(Open sharp media library)
   </div>
  </td>
 </tr>
 </tbody>
</table>
</div>
<!-- end header part -->
<!-- Generated by Doxygen 1.8.15 -->
<script type="text/javascript">
/* @license magnet:?xt=urn:btih:cf05388f2679ee054f2beb29a391d25f4e673ac3&amp;dn=gpl-2.0.txt GPL-v2 */
var searchBox = new SearchBox("searchBox", "search",false,'Search');
/* @license-end */
</script>
<script type="text/javascript" src="menudata.js"></script>
<script type="text/javascript" src="menu.js"></script>
<script type="text/javascript">
/* @license magnet:?xt=urn:btih:cf05388f2679ee054f2beb29a391d25f4e673ac3&amp;dn=gpl-2.0.txt GPL-v2 */
$(function() {
  initMenu('',true,false,'search.php','Search');
  $(document).ready(function() { init_search(); });
});
/* @license-end */</script>
<div id="main-nav"></div>
<!-- window showing the filter options -->
<div id="MSearchSelectWindow"
     onmouseover="return searchBox.OnSearchSelectShow()"
     onmouseout="return searchBox.OnSearchSelectHide()"
     onkeydown="return searchBox.OnSearchSelectKey(event)">
</div>

<!-- iframe showing the search results (closed by default) -->
<div id="MSearchResultsWindow">
<iframe src="javascript:void(0)" frameborder="0" 
        name="MSearchResults" id="MSearchResults">
</iframe>
</div>

</div><!-- top -->
<div class="PageDoc"><div class="header">
  <div class="headertitle">
<div class="title">Osml (Open sharp media library) project </div>  </div>
</div><!--header-->
<div class="contents">
<div class="textblock"><p><a href="https://www.codefactor.io/repository/github/nullcharmander/osml"><img src="https://www.codefactor.io/repository/github/nullcharmander/osml/badge" alt="CodeFactor" class="inline"/>
</a></p>
<p>C# and C based library made for easy media management.</p>
<h2>Notes</h2>
<ul>
<li>This library is in experimental phase, and many things may break.</li>
<li><a class="el" href="namespaceOSML.html">OSML</a> was not tested on windows, so Linux is only supported platform(for now).</li>
<li>C code needs to be rewritten.</li>
</ul>
<h2>Feature list</h2>
<p>this is work in progress</p>
<h3>Main</h3>
<ul>
<li>[x] Media caching using XML and SQLite</li>
<li>[ ] Log support(OsmlLog)</li>
<li>[ ] Settings storage support</li>
</ul>
<h3>Audio</h3>
<ul>
<li>[x] Main Audio support</li>
<li>[x] D3V2 metadata support</li>
<li>[x] ID3V1 metadata support</li>
<li>[x] Albums support</li>
<li>[x] Artist support</li>
<li>[ ] Playlist support</li>
<li>[ ] Extensible Metadata Platform (XMP)</li>
</ul>
<h3>Planned features</h3>
<blockquote class="doxtable">
<p>See Usage (Videos(movies) and images(pictures)) part see more info about audio and video support. </p>
</blockquote>
<ul>
<li>[ ] Audio formats</li>
<li>[ ] Video formats</li>
</ul>
<h2>Usage</h2>
<h3>Initialization</h3>
<p>Reference osml library to your app, and execute Initialization with following line:</p>
<pre class="fragment">await OSML.Initialization.Run()
</pre><p>This will create main <a class="el" href="namespaceOSML.html">OSML</a> folder(used for caching and other stuff) and initialize cache(databases, etc...).</p>
<p>Osml does not contain default searching(caching) folders, but you can add some with following line of code: </p><pre class="fragment">OSML.Cache.CacheManager.AddAsync("folder_path_here").Wait();
</pre><blockquote class="doxtable">
<p>Media database will be automatically updated. </p>
</blockquote>
<h2></h2>
<h3>Getting audio(music)</h3>
<p>After cache is initialized you can get your music using: </p><pre class="fragment">OSML.Data.Music.OSMLAudioData.AllMusic;
</pre><h4>Filters:</h4>
<h5>Filtered by artist name:</h5>
<pre class="fragment">OSML.Data.Music.OSMLAudioData.GetFromArtist("artist_name");
</pre><h5>Filtered by album:</h5>
<pre class="fragment">OSML.Data.Music.OSMLAudioData.GetFromAlbum("album_name");
</pre><h5>Filtered by year:</h5>
<pre class="fragment">OSML.Data.Music.OSMLAudioData.GetFromYear("year");
</pre><h2></h2>
<h3>Videos(movies) and images(pictures)</h3>
<p>Video and image formats are not supported(yet). While those formats are unsupported, osml still caches files and only loads them as MediaObj(so no sql(slow)), which means only bare bones data is available. Here is how to get video files: </p><pre class="fragment">foreach(Cache.CacheObj c_obj in Cache.CurrentCData.FolderList) {
    foreach(Media.MediaObj m_obj in c_obj.Media) {
        if(m_obj.Type == Media.MediaType.Video_Movies) {
            System.Console.WriteLine(m_obj.Path);
        }
    }
}
</pre><p>And here is how to get image files(Just change Media.MediaType.Video_Movies to Media.MediaType.Images_Pictures) </p><pre class="fragment">foreach(Cache.CacheObj c_obj in Cache.CurrentCData.FolderList) {
    foreach(Media.MediaObj m_obj in c_obj.Media) {
        if(m_obj.Type == Media.MediaType.Images_Pictures) {
            System.Console.WriteLine(m_obj.Path);
        }
    }
}
</pre><h1>How to contribute</h1>
<h2>Prerequisites</h2>
<ul>
<li>Minimum .NET Core SDK version 2.2 installed</li>
<li>Linux distribution that supports .NET Core(Windows is not supported at this moment)</li>
</ul>
<h3>Clone repository</h3>
<p>Open terminal and type:</p>
<p>git clone <a href="https://github.com/NULLCharmander/osml">https://github.com/NULLCharmander/osml</a></p>
<p>This will clone osml to home directory, or to any other currently opened folder in terminal</p>
<h3>Tests</h3>
<p>Not available.</p>
<h3>Pull request</h3>
<p>Create pull request with description about changes </p>
</div></div><!-- PageDoc -->
</div><!-- contents -->
<!-- start footer part -->
<hr class="footer"/><address class="footer"><small>
Generated by &#160;<a href="http://www.doxygen.org/index.html">
<img class="footer" src="doxygen.png" alt="doxygen"/>
</a> 1.8.15
</small></address>
</body>
</html>
