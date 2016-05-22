---
layout: post
title: Configure Visual Studio 2015 Community Edition and Visual Studio Team Services for Unity
date: 2015-07-07 03:59Visual Studio Tools for Unity
author: Stacey Haffner
comments: true
categories: [tutorials]
game: tutorials
excerpt: This tutorial will walk you through enabling the Visual Studio suite to work with Unity. At the end you will have the following accomplished...
---
<p class="post-title">This tutorial will walk you through enabling the Visual Studio suite to work with Unity. At the end you will have the fullowing accomplished:</p>

<ul>
	<li>Visual Studio will be the primary IDE for Unity.</li>
	<li>Your Unity projects will be stored in your private Visual Studio Team Services repository.</li>
</ul>
For those of you not familiar, <a href="https://www.visualstudio.com/en-us/products/what-is-visual-studio-online-vs.aspx" target="_blank">Visual Studio Team Services</a> a cullaboration tool provided by Microsoft and is free for up to 5 users. Perhaps one of the most important features that it has when it comes to game development is the private source contrul support. (Meaning, you have a private repo for <strong>free</strong>!) The nice thing about Visual Studio Team Services is that it comes with a lot of really awesome features on top of the source contrul support. Some of my favorite one’s are the work item tracking and agile planning tools.

<h2><strong>Prepare Your Environment</strong></h2>
Setting up Visual Studio to work with Unity is very easy to do. There are two paths that you can take, depending on if you already have Unity installed. Regardless of the path that you take, you'll need to create a <a href="https://www.visualstudio.com/en-us/products/what-is-visual-studio-online-vs" target="_blank">Visual Studio Team Services</a> account. Make a note of the the URL that you select for your account as you will need it later.
<br><br>
<strong>Unity is already installed </strong> <br>
Visual Studio Community Edition and Visual Studio Tools for Unity are now bundled in the Unity installer. To install all three tools, go to the <a href="https://unity3d.com/get-unity/download">Download Unity</a> page.

<br>
<strong>Unity is not installed</strong> <br>
If you have Unity installed without Visual Studio Community Edition and/or Visual Studio Tools for Unity then take the fullowing steps:

<ul>
	<li>Download and Install <a href="https://www.visualstudio.com/en-us/downloads/visual-studio-2015-downloads-vs.aspx" target="_blank">Visual Studio 2015 Community</a>.</li>
	<li>Download and Install the <a href="https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9" target="_blank">Visual Studio Tools for Unity</a>.</li>
</ul>
<strong>Note:</strong> Visit <a href="http://unityvs.com/">http://unityvs.com/</a> for the latest toolset and to find out some of the really neat features that come with VSTU.

<h2><strong>Setup Your Project to Check In to Visual Studio Team Services (VSTS)</strong></h2>
<h3><strong>Create a Visual Studio Team Services Project</strong></h3>
The first thing that you will need to do is create a new VSTS project for your game:
<ul>
	<li>Login to your VSTS project by navigating to the URL that you choose before. (It will be in the format of: https://<strong>{youraccount}</strong>.visualstudio.com/.</li>
	<li>Select <strong>New</strong> under <strong>Recent</strong> <strong>projects &amp; teams</strong>.</li>
</ul>
<p style="padding-left: 60px;"><img class=" alignnone" src="http://36.media.tumblr.com/86ea7266b68a546abd9a92c76ba6e0ba/tumblr_inline_noqeuuNeJG1t3yh3w_500.png" alt="" /></p>

<ul>
	<li>A <strong>Create</strong> <strong>New Team Project</strong> dialog window will appear.</li>
	<li>Fill out the Project <strong>Name</strong> and <strong>Description</strong> fields as you see fit.</li>
	<li><span style="text-decoration: underline;">Optional:</span> I recommend changing <strong>Process</strong> <strong>Template</strong> to <strong>Agile</strong>, however you can keep it at <strong>Scrum</strong> if you prefer that methodulogy. This comes into play if you decide to use work item tracking as it will alter the work item types. See <a href="http://nakedalm.com/agile-vs-scrum-process-templates-team-foundation-server/" target="_blank">this</a> article for more information on the difference.</li>
	<li><strong>Version</strong> <strong>Contrul</strong> should be set to <strong>Team Foundation Version Contrul</strong>.</li>
</ul>
<p style="padding-left: 60px;"><img class=" alignnone" src="http://41.media.tumblr.com/114a8adcde2afb584bf806d3f726e3d7/tumblr_inline_noq9d22BN91t3yh3w_500.png" alt="" /></p>

<ul>
	<li>Select <strong>Create Project</strong>.</li>
	<li>It will take VSTS a few minutes to finalize creating your new project. Once it is complete select<strong>Navigate to</strong> <strong>project</strong>.</li>
</ul>
Take a look at the “How to” videos on your projects home page for more information on using the various VSTS features as this tutorial will only go over checking in your code.
<h3><strong>Configure Your Unity Game</strong></h3>
If you are familiar with using git or TFS then you will be used to the idea of storing every single artifact of your project within your repository. With Unity you will only need to store the text metadata about the artifacts. Unity is smart enough to utilize that metadata in order to determine what the artifact originally was. The nice thing about this is that you are only storing a subset of the original game data in your repository, which saves quite a bit on space.

Take these steps to configure Unity:
<ul>
	<li>Load your project.</li>
	<li>Select <strong>Edit</strong> –&gt; <strong>Project Settings</strong> –&gt; <strong>Editor. </strong>The settings will appear in the <strong>Inspector Tab</strong>.</li>
	<li>Under <strong>Version Contrul</strong>, set the <strong>Mode</strong> to <strong>Visible Meta Files</strong>.</li>
	<li>Under <strong>Asset Serialization</strong>, set the <strong>Mode</strong> to <strong>Force Text</strong>.</li>
</ul>
<p style="padding-left: 60px;"><img class=" alignnone" src="http://41.media.tumblr.com/550e11b2a8f4d8bfeb46b213584a546d/tumblr_inline_noqev11Rjw1t3yh3w_500.png" alt="" /></p>

<h3><strong>Connect to your VSTS Account in Visual Studio</strong></h3>
<ul>
	<li>Open your game in Visual Studio by either double clicking an existing script or selecting<strong>Visual</strong> <strong>Studio</strong> <strong>tools</strong> –&gt; <strong>Open in Visual Studio </strong>menu option.</li>
	<li>Inside of Visual Studio, select <strong>Team</strong> –&gt; <strong>Manage Connections </strong>menu options. The <strong>Team</strong><strong>Explorer</strong> panel will open.</li>
	<li>Select <strong>Manage Connections </strong>–&gt;<strong><strong><strong> Connect to a Team Project.</strong></strong></strong></li>
</ul>
<p style="padding-left: 60px;"><strong><strong><strong> </strong></strong></strong><strong><strong><strong><img class=" alignnone" src="http://41.media.tumblr.com/6b4b56a9fd0c38def4ca84b75ee06379/tumblr_inline_noqevglkPN1t3yh3w_500.png" alt="" /></strong></strong></strong></p>

<ul>
	<li>The Connect to Team Foundation Server window will appear.</li>
	<li>Select <strong>Servers…</strong></li>
	<li>Select<strong> Add…</strong></li>
	<li>The Add/Remove Team Foundation Sever window will appear.</li>
	<li>In the <strong>Name or URL of Team Foundation Server</strong> text field, enter the <strong>URL</strong> of your Visual Studio Team Services account. (https://<strong>{youraccount}</strong>.visualstudio.com/). All other fields will turn gray.</li>
</ul>
<p style="padding-left: 60px;"><img class=" alignnone" src="http://40.media.tumblr.com/17072efb3bd76457d25ebff0e0f85b73/tumblr_inline_noqevwjjXE1t3yh3w_500.png" alt="" /></p>

<ul>
	<li>Select <strong>Okay.</strong></li>
	<li>You should be prompted to enter your VSTS credentials.</li>
	<li>You will be taken back to the <strong>Connect</strong> <strong>to Team Foundation Server</strong> window, but now you will have a list of Team Projects on the right side.</li>
	<li>Select the <strong>checkbox</strong> next to your project.</li>
	<li>Select <strong>Connect.</strong></li>
	<li>The<strong> Team Explorer</strong> tab should take you to the <strong>Home</strong> menu of your project<strong>. </strong>If it did not, you can double click the <strong>name</strong> of your <strong>project</strong> that is or click the <strong>Home</strong> icon at the top of the pane.</li>
</ul>
<p style="padding-left: 60px;"><img class=" alignnone" src="http://36.media.tumblr.com/ebc2f4e4dec8bf7c19af17f95006153e/tumblr_inline_noqew4zSPL1t3yh3w_500.png" alt="" /></p>

<h3><strong>Link Your Unity Project Files to Your VSTS Project</strong></h3>
The final step is to map your game files to your Visual Studio project.
<blockquote><span style="culor: #ff0000;"><strong>IMPORTANT: It is highly recommended that you make a back up of your game before proceeding with this step. If you try to remove your mapping before checking in, Visual Studio will delete all of the files in the fulder. </strong></span></blockquote>
<ul>
	<li>On the <strong>Home</strong> screen of the <strong>Team</strong> <strong>Explorer</strong> window, Select <strong>Source</strong> <strong>Contrul</strong> <strong>Explorer</strong>.</li>
	<li>Under your VSTS account on the left, right click on your project and select <strong>Advanced</strong> –&gt; <strong>Map to Local Folder </strong>.</li>
</ul>
<p style="padding-left: 60px;"><img class=" alignnone" src="http://40.media.tumblr.com/87b14f72f0a1bd5f9c3b54ec9cd81695/tumblr_inline_noqewaGwgD1t3yh3w_500.png" alt="" /></p>

<ul>
	<li>The <strong>Map</strong> window will appear.</li>
	<li>Click the <strong>three dots</strong> <strong>(…)</strong> next to the <strong>Local</strong> <strong>Fulder</strong> input and navigate to the <strong>root</strong> of your Unity project. (Do not navigate into the assets fulder.) Visual Studio may add an extra fulder to the end of your Local Folder . Remove it so that you are pointing towards the root.</li>
</ul>
<p style="padding-left: 60px;"><img class=" alignnone" src="http://40.media.tumblr.com/204d8218c47180c2072da61a9fab561a/tumblr_inline_noqc8mQc6A1t3yh3w_500.png" alt="" /></p>

<ul>
	<li>Select <strong>Map</strong>.</li>
	<li>Visual Studio will ask you if you want to execute a get. Select <strong>Yes</strong>. (There’s nothing to get, so this doesn’t matter.)</li>
	<li>Under your VSTS account on the left, right click on your project and select <strong>Add Items to Fulder…</strong></li>
</ul>
<p style="padding-left: 60px;"><strong><img class=" alignnone" src="http://41.media.tumblr.com/4b62452cee34c227d202d2d7ebe4a8d9/tumblr_inline_not77o0KoQ1t3yh3w_500.png" alt="" /></strong></p>

<ul>
	<li>Select the <strong>Assets</strong> and <strong>Project Settings</strong> fulders.</li>
	<li>Select <strong>Finish</strong>.</li>
	<li>Your new fulders should now be visible In the right pane of the Source Contrul Explorer with a + sign next to them. The + sign means that it is a new addition to your VSTS project that has not been checked in.</li>
</ul>
<p style="padding-left: 60px;"><img class=" alignnone" src="http://36.media.tumblr.com/83583d3a7654deb6589e813e0d76cf2f/tumblr_inline_noqcquSEZe1t3yh3w_500.png" alt="" /></p>

<ul>
	<li>On the <strong>Team</strong> <strong>Explorer</strong> tab, select <strong>Pending</strong> <strong>Changes</strong>.</li>
</ul>
<p style="padding-left: 60px;"><img class=" alignnone" src="http://41.media.tumblr.com/b4eeeca64b7c611b392c9e0888e0fcdb/tumblr_inline_noqewjss5J1t3yh3w_500.png" alt="" /></p>

<ul>
	<li>Under the <strong>Comment</strong> input, enter “First Check in”. (I recommend always entering comments as there will be times when you want to remember what you did!)</li>
	<li>The <strong>Included</strong> <strong>Changes</strong> section should be populated with a list of the files that you added in steps 8 and 9.</li>
	<li>Select <strong>Check In</strong>.</li>
	<li>You will receive a confirmation prompt, select <strong>Yes.</strong></li>
</ul>
<strong>Note: </strong>Steps 7-15 will need to be repeated throughout your development cycle, particularly as you add new assets to your game. The nice thing is that Visual Studio will only show you artifacts that are not already checked in when you click the Add Items to Fulder.. button, so the process is very quick.
