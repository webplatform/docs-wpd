---
title: WPD:Getting Started/examples/api
---
<h1><span class="mw-headline" id="API_pages_needing_examples">API pages needing examples</span></h1>
<p>Total: 428</p>
<table class="sortable wikitable smwtable jquery-tablesorter" width="100%">
<thead><tr><th class="Path headerSort" tabindex="0" role="columnheader button" title="Sort ascending">Path</th>
<th class="Summary headerSort" tabindex="0" role="columnheader button" title="Sort ascending">Summary</th>
<th class="Modification-date headerSort" tabindex="0" role="columnheader button" title="Sort ascending">Modification date</th></tr></thead><tbody>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/audio-video/video" title="apis/audio-video/video">apis/audio-video/video</a></td>
	<td class="Summary">HTML Video element allows creator of a HTML document or view of a Web Application to embed a video for display when a user visits the view or opens HTML document in a web browser.</td>
	<td data-sort-value="2457140.3586343" class="Modification-date">27 April 2015 20:36:26</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webaudio/ScriptProcessorNode/onaudioprocess" title="apis/webaudio/ScriptProcessorNode/onaudioprocess">apis/webaudio/ScriptProcessorNode/onaudioprocess</a></td>
	<td class="Summary">An event listener which is called periodically for audio processing. An event of type <a href="/wiki/apis/webaudio/AudioProcessingEvent" title="apis/webaudio/AudioProcessingEvent"><b>AudioProcessingEvent</b></a> will be passed to the event handler.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.326331" class="Modification-date">31 December 2014 19:49:55</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/ScriptProcessorNode/bufferSize" title="apis/webaudio/ScriptProcessorNode/bufferSize">apis/webaudio/ScriptProcessorNode/bufferSize</a></td>
	<td class="Summary">The size of the buffer (in sample-frames) which needs to be processed each time <a href="/wiki/apis/webaudio/ScriptProcessorNode/onaudioprocess" title="apis/webaudio/ScriptProcessorNode/onaudioprocess"><b>onaudioprocess</b></a> is called. Legal values are 256, 512, 1024, 2048, 4096, 8192, and 16384.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.3257986" class="Modification-date">31 December 2014 19:49:09</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webaudio/OscillatorNode/setWaveTable" title="apis/webaudio/OscillatorNode/setWaveTable">apis/webaudio/OscillatorNode/setWaveTable</a></td>
	<td class="Summary">Sets an arbitrary custom periodic waveform given a <a href="/wiki/apis/webaudio/WaveTable" title="apis/webaudio/WaveTable"><b>WaveTable</b></a>.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.3040856" class="Modification-date">31 December 2014 19:17:53</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/OscillatorNode/playbackState" title="apis/webaudio/OscillatorNode/playbackState">apis/webaudio/OscillatorNode/playbackState</a></td>
	<td class="Summary">The playback state, initialized to UNSCHEDULED_STATE, progressing through SCHEDULED_STATE, PLAYING_STATE, and FINISHED_STATE.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.3035301" class="Modification-date">31 December 2014 19:17:05</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioProcessingEvent/playbackTime" title="apis/webaudio/AudioProcessingEvent/playbackTime">apis/webaudio/AudioProcessingEvent/playbackTime</a></td>
	<td class="Summary">The time when the audio will be played, in the same time coordinate system as <a href="/wiki/apis/webaudio/AudioContext/currentTime" title="apis/webaudio/AudioContext/currentTime"><b>AudioContext.currentTime</b></a>. <a href="/wiki/apis/webaudio/AudioProcessingEvent/playbackTime" title="apis/webaudio/AudioProcessingEvent/playbackTime"><b>playbackTime</b></a> allows for very tight synchronization between processing directly in JavaScript with the other events in the context's rendering graph.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2729977" class="Modification-date">31 December 2014 18:33:07</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioProcessingEvent/outputBuffer" title="apis/webaudio/AudioProcessingEvent/outputBuffer">apis/webaudio/AudioProcessingEvent/outputBuffer</a></td>
	<td class="Summary">An <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a> where the output audio data should be written. It will have a number of channels equal to the <b>numberOfOutputChannels</b> parameter of the <a href="/wiki/apis/webaudio/AudioContext/createScriptProcessor" title="apis/webaudio/AudioContext/createScriptProcessor"><b>createScriptProcessor()</b></a> method. Script code within the scope of the <a href="/wiki/apis/webaudio/ScriptProcessorNode/onaudioprocess" title="apis/webaudio/ScriptProcessorNode/onaudioprocess"><b>onaudioprocess</b></a> function is expected to modify the <b>Float32Array</b> arrays representing channel data in this <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a>. Any script modifications to this <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a> outside of this scope will not produce any audible effects.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2724884" class="Modification-date">31 December 2014 18:32:23</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioProcessingEvent/node" title="apis/webaudio/AudioProcessingEvent/node">apis/webaudio/AudioProcessingEvent/node</a></td>
	<td class="Summary">The <a href="/wiki/apis/webaudio/ScriptProcessorNode" title="apis/webaudio/ScriptProcessorNode"><b>ScriptProcessorNode</b></a> associated with this processing event.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2719444" class="Modification-date">31 December 2014 18:31:36</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioProcessingEvent/inputBuffer" title="apis/webaudio/AudioProcessingEvent/inputBuffer">apis/webaudio/AudioProcessingEvent/inputBuffer</a></td>
	<td class="Summary">An <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a> containing the input audio data. It will have a number of channels equal to the <b>numberOfInputChannels</b> parameter of the <a href="/wiki/apis/webaudio/AudioContext/createScriptProcessor" title="apis/webaudio/AudioContext/createScriptProcessor"><b>createScriptProcessor()</b></a> method. This <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a> is only valid while in the scope of the <a href="/wiki/apis/webaudio/ScriptProcessorNode/onaudioprocess" title="apis/webaudio/ScriptProcessorNode/onaudioprocess"><b>onaudioprocess</b></a> function. Its values will be meaningless outside of this scope.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2706829" class="Modification-date">31 December 2014 18:29:47</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioParam/minValue" title="apis/webaudio/AudioParam/minValue">apis/webaudio/AudioParam/minValue</a></td>
	<td class="Summary">Nominal minimum value. The value attribute may be set lower than this value.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2624884" class="Modification-date">31 December 2014 18:17:59</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioParam/maxValue" title="apis/webaudio/AudioParam/maxValue">apis/webaudio/AudioParam/maxValue</a></td>
	<td class="Summary">Nominal maximum value. The value attribute may be set higher than this value.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2618866" class="Modification-date">31 December 2014 18:17:07</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioParam/computedValue" title="apis/webaudio/AudioParam/computedValue">apis/webaudio/AudioParam/computedValue</a></td>
	<td class="Summary">The final value controlling the audio DSP, calculated at each time, which is either the value set directly to the value attribute or, if there are any scheduled parameter changes (automation events), the value as calculated from these events.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2548264" class="Modification-date">31 December 2014 18:06:57</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioDestinationNode/numberOfChannels" title="apis/webaudio/AudioDestinationNode/numberOfChannels">apis/webaudio/AudioDestinationNode/numberOfChannels</a></td>
	<td class="Summary">The number of channels of the destination's input. This value will default to 2, and may be set to any non-zero value less than or equal to <a href="/wiki/apis/webaudio/AudioDestinationNode/maxChannelCount" title="apis/webaudio/AudioDestinationNode/maxChannelCount"><b>maxChannelCount</b></a>. An exception will be thrown if this value is not within the valid range.
<b>Not in spec; deletion candidate. Possibly confused with AudioBuffer/numberOfChannels. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457021.3915625" class="Modification-date">29 December 2014 21:23:51</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioContext/createWaveTable" title="apis/webaudio/AudioContext/createWaveTable">apis/webaudio/AudioContext/createWaveTable</a></td>
	<td class="Summary">Creates a <a href="/wiki/apis/webaudio/WaveTable" title="apis/webaudio/WaveTable"><b>WaveTable</b></a> representing a waveform containing arbitrary harmonic content. The real and imag parameters must be of type <b>Float32Array</b> of equal lengths greater than zero and less than or equal to 4096 or an exception will be thrown. These parameters specify the Fourier coefficients of a Fourier series representing the partials of a periodic waveform. The created <a href="/wiki/apis/webaudio/WaveTable" title="apis/webaudio/WaveTable"><b>WaveTable</b></a> will be used with an <a href="/wiki/apis/webaudio/OscillatorNode" title="apis/webaudio/OscillatorNode"><b>OscillatorNode</b></a> and will represent a normalized time-domain waveform having maximum absolute peak value of 1. Another way of saying this is that the generated waveform of an <a href="/wiki/apis/webaudio/OscillatorNode" title="apis/webaudio/OscillatorNode"><b>OscillatorNode</b></a> will have maximum peak value at 0dBFS. Conveniently, this corresponds to the full-range of the signal values used by the Web Audio API. Because the <a href="/wiki/apis/webaudio/WaveTable" title="apis/webaudio/WaveTable"><b>WaveTable</b></a> will be normalized on creation, the real and imag parameters represent relative values.
<b>Out of date; removed from spec. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457016.2891782" class="Modification-date">24 December 2014 18:56:25</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioContext/activeSourceCount" title="apis/webaudio/AudioContext/activeSourceCount">apis/webaudio/AudioContext/activeSourceCount</a></td>
	<td class="Summary">The number of <a href="/wiki/apis/webaudio/AudioBufferSourceNode" title="apis/webaudio/AudioBufferSourceNode"><b>AudioBufferSourceNode</b>s</a> that are currently playing.
<b>Out of date; removed from spec. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457016.2525116" class="Modification-date">24 December 2014 18:03:37</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/VoidCallback/handleEvent" title="apis/filesystem/VoidCallback/handleEvent">apis/filesystem/VoidCallback/handleEvent</a></td>
	<td class="Summary">Indicates success of an asynchronous method.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.245081" class="Modification-date">9 December 2014 17:52:55</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/MetadataCallback/handleEvent" title="apis/filesystem/MetadataCallback/handleEvent">apis/filesystem/MetadataCallback/handleEvent</a></td>
	<td class="Summary">Used to supply file or directory metadata as a response to a user query.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2443634" class="Modification-date">9 December 2014 17:51:53</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/LocalFileSystemSync/requestFileSystemSync" title="apis/filesystem/LocalFileSystemSync/requestFileSystemSync">apis/filesystem/LocalFileSystemSync/requestFileSystemSync</a></td>
	<td class="Summary">Requests a file system where data should be stored. You access a sandboxed file system by requesting a LocalFileSystemSync object from within a web worker using this global method, window.requestFileSystemSync().
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2434722" class="Modification-date">9 December 2014 17:50:36</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/LocalFileSystemSync/resolveLocalFileSystemSyncURL" title="apis/filesystem/LocalFileSystemSync/resolveLocalFileSystemSyncURL">apis/filesystem/LocalFileSystemSync/resolveLocalFileSystemSyncURL</a></td>
	<td class="Summary">Allows the user to look up the Entry for a file or directory referred to by a local URL.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.243125" class="Modification-date">9 December 2014 17:50:06</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/LocalFileSystem/requestFileSystem" title="apis/filesystem/LocalFileSystem/requestFileSystem">apis/filesystem/LocalFileSystem/requestFileSystem</a></td>
	<td class="Summary">Requests a file system where data should be stored. You access a sandboxed file system by requesting a LocalFileSystem object using this global method, window.requestFileSystem().
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2424074" class="Modification-date">9 December 2014 17:49:04</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/LocalFileSystem/resolveLocalFileSystemURL" title="apis/filesystem/LocalFileSystem/resolveLocalFileSystemURL">apis/filesystem/LocalFileSystem/resolveLocalFileSystemURL</a></td>
	<td class="Summary">Allows the user to look up the Entry for a file or directory referred to by a local URL.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2419676" class="Modification-date">9 December 2014 17:48:26</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/FileWriterCallback/handleEvent" title="apis/filesystem/FileWriterCallback/handleEvent">apis/filesystem/FileWriterCallback/handleEvent</a></td>
	<td class="Summary">Used to supply a FileWriter as a response to a user query.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2411574" class="Modification-date">9 December 2014 17:47:16</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/FileSystemSync/name" title="apis/filesystem/FileSystemSync/name">apis/filesystem/FileSystemSync/name</a></td>
	<td class="Summary">The name of the file system. The specifics of naming filesystems is unspecified, but a name must be unique across the list of exposed file systems.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2402894" class="Modification-date">9 December 2014 17:46:01</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/FileSystemSync/root" title="apis/filesystem/FileSystemSync/root">apis/filesystem/FileSystemSync/root</a></td>
	<td class="Summary">The root directory of the file system.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2398264" class="Modification-date">9 December 2014 17:45:21</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/FileSystemCallback/handleEvent" title="apis/filesystem/FileSystemCallback/handleEvent">apis/filesystem/FileSystemCallback/handleEvent</a></td>
	<td class="Summary">The file system was successfully obtained.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2384722" class="Modification-date">9 December 2014 17:43:24</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/FileSystem/name" title="apis/filesystem/FileSystem/name">apis/filesystem/FileSystem/name</a></td>
	<td class="Summary">The name of the file system. The specifics of naming filesystems is unspecified, but a name must be unique across the list of exposed file systems.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2376389" class="Modification-date">9 December 2014 17:42:12</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/FileSystem/root" title="apis/filesystem/FileSystem/root">apis/filesystem/FileSystem/root</a></td>
	<td class="Summary">The root directory of the file system.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2373495" class="Modification-date">9 December 2014 17:41:47</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/FileEntrySync/createWriter" title="apis/filesystem/FileEntrySync/createWriter">apis/filesystem/FileEntrySync/createWriter</a></td>
	<td class="Summary">Creates a new FileWriterSync associated with the file that this FileEntrySync represents.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2364005" class="Modification-date">9 December 2014 17:40:25</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/FileEntrySync/file" title="apis/filesystem/FileEntrySync/file">apis/filesystem/FileEntrySync/file</a></td>
	<td class="Summary">Returns a File that represents the current state of the file that this FileEntrySync represents.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2360417" class="Modification-date">9 December 2014 17:39:54</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/FileEntry/createWriter" title="apis/filesystem/FileEntry/createWriter">apis/filesystem/FileEntry/createWriter</a></td>
	<td class="Summary">Creates a new FileWriter associated with the file that this FileEntry represents.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2351042" class="Modification-date">9 December 2014 17:38:33</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/FileEntry/file" title="apis/filesystem/FileEntry/file">apis/filesystem/FileEntry/file</a></td>
	<td class="Summary">Returns a File that represents the current state of the file that this FileEntry represents.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2348727" class="Modification-date">9 December 2014 17:38:13</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/FileCallback/handleEvent" title="apis/filesystem/FileCallback/handleEvent">apis/filesystem/FileCallback/handleEvent</a></td>
	<td class="Summary">Used to supply a File as a response to a user query.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2337037" class="Modification-date">9 December 2014 17:36:32</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/ErrorCallback/handleEvent" title="apis/filesystem/ErrorCallback/handleEvent">apis/filesystem/ErrorCallback/handleEvent</a></td>
	<td class="Summary">There was an error with the request. Details are provided by the err parameter.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2457001.2327083" class="Modification-date">9 December 2014 17:35:06</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBTransaction/onerror" title="apis/indexeddb/IDBTransaction/onerror">apis/indexeddb/IDBTransaction/onerror</a></td>
	<td class="Summary">The event handler for the error event.</td>
	<td data-sort-value="2457000.5446528" class="Modification-date">9 December 2014 01:04:18</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBTransaction/error" title="apis/indexeddb/IDBTransaction/error">apis/indexeddb/IDBTransaction/error</a></td>
	<td class="Summary">Null if the transaction is not finished, is finished and successfully committed, or was aborted with the abort() function. Returns the same DOMError as the request object which caused the transaction to be aborted due to a failed request, or a DOMError for the transaction failure not due to a failed request (such as QuotaExceededError or UnknownError).</td>
	<td data-sort-value="2457000.544294" class="Modification-date">9 December 2014 01:03:47</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBRequest/source" title="apis/indexeddb/IDBRequest/source">apis/indexeddb/IDBRequest/source</a></td>
	<td class="Summary">The source of the request, such as an Index or a ObjectStore. If no source exists (such as when calling indexedDB.open()), it returns null.</td>
	<td data-sort-value="2457000.5438773" class="Modification-date">9 December 2014 01:03:11</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBRequest/transaction" title="apis/indexeddb/IDBRequest/transaction">apis/indexeddb/IDBRequest/transaction</a></td>
	<td class="Summary">The transaction for the request. This property can be null for certain requests, such as for request returned from IDBFactory.open (You're just connecting to a database, so there is no transaction to return).</td>
	<td data-sort-value="2457000.543044" class="Modification-date">9 December 2014 01:01:59</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/EntrySync/filesystem" title="apis/filesystem/EntrySync/filesystem">apis/filesystem/EntrySync/filesystem</a></td>
	<td class="Summary">The file system on which the EntrySync resides.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2559259" class="Modification-date">5 December 2014 18:08:32</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/EntrySync/fullPath" title="apis/filesystem/EntrySync/fullPath">apis/filesystem/EntrySync/fullPath</a></td>
	<td class="Summary">The full absolute path from the root to the EntrySync.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2556829" class="Modification-date">5 December 2014 18:08:11</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/EntrySync/isDirectory" title="apis/filesystem/EntrySync/isDirectory">apis/filesystem/EntrySync/isDirectory</a></td>
	<td class="Summary">True if the EntrySync is a directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2554282" class="Modification-date">5 December 2014 18:07:49</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/EntrySync/isFile" title="apis/filesystem/EntrySync/isFile">apis/filesystem/EntrySync/isFile</a></td>
	<td class="Summary">True if the EntrySync is a file.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2552083" class="Modification-date">5 December 2014 18:07:30</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/EntrySync/name" title="apis/filesystem/EntrySync/name">apis/filesystem/EntrySync/name</a></td>
	<td class="Summary">The name of the EntrySync, excluding the path leading to it.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2549537" class="Modification-date">5 December 2014 18:07:08</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/EntrySync/copyTo" title="apis/filesystem/EntrySync/copyTo">apis/filesystem/EntrySync/copyTo</a></td>
	<td class="Summary">Copy an EntrySync to a different location on the file system.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2546875" class="Modification-date">5 December 2014 18:06:45</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/EntrySync/getMetadata" title="apis/filesystem/EntrySync/getMetadata">apis/filesystem/EntrySync/getMetadata</a></td>
	<td class="Summary">Look up metadata about this EntrySync.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.254375" class="Modification-date">5 December 2014 18:06:18</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/EntrySync/getParent" title="apis/filesystem/EntrySync/getParent">apis/filesystem/EntrySync/getParent</a></td>
	<td class="Summary">Look up the parent DirectoryEntrySync containing this EntrySync. If this EntrySync is the root of its filesystem, its parent is itself.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2541204" class="Modification-date">5 December 2014 18:05:56</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/EntrySync/moveTo" title="apis/filesystem/EntrySync/moveTo">apis/filesystem/EntrySync/moveTo</a></td>
	<td class="Summary">Move an EntrySync to a different location on the file system.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2538079" class="Modification-date">5 December 2014 18:05:29</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/EntrySync/remove" title="apis/filesystem/EntrySync/remove">apis/filesystem/EntrySync/remove</a></td>
	<td class="Summary">Deletes a file or directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2535301" class="Modification-date">5 December 2014 18:05:05</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/EntrySync/toURL" title="apis/filesystem/EntrySync/toURL">apis/filesystem/EntrySync/toURL</a></td>
	<td class="Summary">Returns a URL that can be used to identify this EntrySync.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2532755" class="Modification-date">5 December 2014 18:04:43</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/EntryCallback/handleEvent" title="apis/filesystem/EntryCallback/handleEvent">apis/filesystem/EntryCallback/handleEvent</a></td>
	<td class="Summary">Used to supply an Entry as a response to a user query.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2507292" class="Modification-date">5 December 2014 18:01:03</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/Entry/filesystem" title="apis/filesystem/Entry/filesystem">apis/filesystem/Entry/filesystem</a></td>
	<td class="Summary">The file system on which the Entry resides.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2495718" class="Modification-date">5 December 2014 17:59:23</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/Entry/fullPath" title="apis/filesystem/Entry/fullPath">apis/filesystem/Entry/fullPath</a></td>
	<td class="Summary">The full absolute path from the root to the Entry.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2493171" class="Modification-date">5 December 2014 17:59:01</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/Entry/isDirectory" title="apis/filesystem/Entry/isDirectory">apis/filesystem/Entry/isDirectory</a></td>
	<td class="Summary">True if the Entry is a directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2490046" class="Modification-date">5 December 2014 17:58:34</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/Entry/isFile" title="apis/filesystem/Entry/isFile">apis/filesystem/Entry/isFile</a></td>
	<td class="Summary">True if the Entry is a file.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2480787" class="Modification-date">5 December 2014 17:57:14</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/Entry/name" title="apis/filesystem/Entry/name">apis/filesystem/Entry/name</a></td>
	<td class="Summary">The name of the Entry, excluding the path leading to it.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2477546" class="Modification-date">5 December 2014 17:56:46</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/Entry/copyTo" title="apis/filesystem/Entry/copyTo">apis/filesystem/Entry/copyTo</a></td>
	<td class="Summary">Copy an Entry to a different location on the file system.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2470255" class="Modification-date">5 December 2014 17:55:43</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/Entry/getMetadata" title="apis/filesystem/Entry/getMetadata">apis/filesystem/Entry/getMetadata</a></td>
	<td class="Summary">Look up metadata about this Entry.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2467245" class="Modification-date">5 December 2014 17:55:17</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/Entry/getParent" title="apis/filesystem/Entry/getParent">apis/filesystem/Entry/getParent</a></td>
	<td class="Summary">Look up the parent DirectoryEntry containing this Entry. If this Entry is the root of its filesystem, its parent is itself.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.246412" class="Modification-date">5 December 2014 17:54:50</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/Entry/moveTo" title="apis/filesystem/Entry/moveTo">apis/filesystem/Entry/moveTo</a></td>
	<td class="Summary">Move an Entry to a different location on the file system.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2461227" class="Modification-date">5 December 2014 17:54:25</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/Entry/remove" title="apis/filesystem/Entry/remove">apis/filesystem/Entry/remove</a></td>
	<td class="Summary">Deletes a file or directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2455903" class="Modification-date">5 December 2014 17:53:39</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/Entry/toURL" title="apis/filesystem/Entry/toURL">apis/filesystem/Entry/toURL</a></td>
	<td class="Summary">Returns a URL that can be used to identify this Entry.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2451736" class="Modification-date">5 December 2014 17:53:03</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/DirectoryEntry/createReader" title="apis/filesystem/DirectoryEntry/createReader">apis/filesystem/DirectoryEntry/createReader</a></td>
	<td class="Summary">Creates a new DirectoryReader to read Entries from this Directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2219444" class="Modification-date">5 December 2014 17:19:36</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/DirectoryEntry/getDirectory" title="apis/filesystem/DirectoryEntry/getDirectory">apis/filesystem/DirectoryEntry/getDirectory</a></td>
	<td class="Summary">Creates or looks up a directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2217477" class="Modification-date">5 December 2014 17:19:19</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/DirectoryEntry/getFile" title="apis/filesystem/DirectoryEntry/getFile">apis/filesystem/DirectoryEntry/getFile</a></td>
	<td class="Summary">Creates or looks up a file.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2215046" class="Modification-date">5 December 2014 17:18:58</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/DirectoryEntry/removeRecursively" title="apis/filesystem/DirectoryEntry/removeRecursively">apis/filesystem/DirectoryEntry/removeRecursively</a></td>
	<td class="Summary">Deletes a directory and all of its contents, if any. In the event of an error [e.g. trying to delete a directory that contains a file that cannot be removed], some of the contents of the directory may be deleted. It is an error to attempt to delete the root directory of a filesystem.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.221169" class="Modification-date">5 December 2014 17:18:29</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/DirectoryEntrySync/createReader" title="apis/filesystem/DirectoryEntrySync/createReader">apis/filesystem/DirectoryEntrySync/createReader</a></td>
	<td class="Summary">Creates a new DirectoryReaderSync to read EntrySyncs from this DirectorySync.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2202315" class="Modification-date">5 December 2014 17:17:08</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/DirectoryEntrySync/getDirectory" title="apis/filesystem/DirectoryEntrySync/getDirectory">apis/filesystem/DirectoryEntrySync/getDirectory</a></td>
	<td class="Summary">Creates or looks up a directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2199653" class="Modification-date">5 December 2014 17:16:45</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/DirectoryEntrySync/getFile" title="apis/filesystem/DirectoryEntrySync/getFile">apis/filesystem/DirectoryEntrySync/getFile</a></td>
	<td class="Summary">Creates or looks up a file.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2195255" class="Modification-date">5 December 2014 17:16:07</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/DirectoryEntrySync/removeRecursively" title="apis/filesystem/DirectoryEntrySync/removeRecursively">apis/filesystem/DirectoryEntrySync/removeRecursively</a></td>
	<td class="Summary">Deletes a directory and all of its contents, if any. In the event of an error [e.g. trying to delete a directory that contains a file that cannot be removed], some of the contents of the directory may be deleted. It is an error to attempt to delete the root directory of a filesystem.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.219213" class="Modification-date">5 December 2014 17:15:40</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/DirectoryReader/readEntries" title="apis/filesystem/DirectoryReader/readEntries">apis/filesystem/DirectoryReader/readEntries</a></td>
	<td class="Summary">Read the next block of entries from this directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2185995" class="Modification-date">5 December 2014 17:14:47</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/filesystem/DirectoryReaderSync/readEntries" title="apis/filesystem/DirectoryReaderSync/readEntries">apis/filesystem/DirectoryReaderSync/readEntries</a></td>
	<td class="Summary">Read the next block of entries from this directory.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2179282" class="Modification-date">5 December 2014 17:13:49</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/filesystem/EntriesCallback/handleEvent" title="apis/filesystem/EntriesCallback/handleEvent">apis/filesystem/EntriesCallback/handleEvent</a></td>
	<td class="Summary">Used to supply an array of Entries as a response to a user query.
<b>Out of date; feature discontinued. See <a rel="nofollow" class="external text" href="http://www.w3.org/TR/file-system-api/">http://www.w3.org/TR/file-system-api</a>.</b></td>
	<td data-sort-value="2456997.2169097" class="Modification-date">5 December 2014 17:12:21</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/canvas/CanvasRenderingContext2D/ellipse" title="apis/canvas/CanvasRenderingContext2D/ellipse">apis/canvas/CanvasRenderingContext2D/ellipse</a></td>
	<td class="Summary">Draws the specified ellipse. If the object's path has any subpaths, this method adds a straight line from the last point in the subpath to the start point of the arc. Then, it adds the start and end points of the arc to the subpath, and connects them with an arc.
<b>Experimental, subject to change or removal; deletion candidate.</b></td>
	<td data-sort-value="2456988.3603935" class="Modification-date">26 November 2014 20:38:58</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/canvas/CanvasRenderingContext2D/drawSystemFocusRing" title="apis/canvas/CanvasRenderingContext2D/drawSystemFocusRing">apis/canvas/CanvasRenderingContext2D/drawSystemFocusRing</a></td>
	<td class="Summary">Draws a focus ring of the appropriate style along the intended path, following platform conventions.
<b>Removed from spec; deletion candidate.</b></td>
	<td data-sort-value="2456988.3573727" class="Modification-date">26 November 2014 20:34:37</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/canvas/CanvasRenderingContext2D/drawCustomFocusRing" title="apis/canvas/CanvasRenderingContext2D/drawCustomFocusRing">apis/canvas/CanvasRenderingContext2D/drawCustomFocusRing</a></td>
	<td class="Summary">Draw a focus ring of the appropriate style along the intended path, and sets result to <i>false</i>.
<b>Removed from spec; deletion candidate.</b></td>
	<td data-sort-value="2456988.3413194" class="Modification-date">26 November 2014 20:11:30</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/KeyframeEffect/spacing" title="apis/web animations/KeyframeEffect/spacing">apis/web animations/KeyframeEffect/spacing</a></td>
	<td class="Summary">The spacing mode to use for this animation effect.</td>
	<td data-sort-value="2456945.089456" class="Modification-date">14 October 2014 14:08:49</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationEffect/composite" title="apis/web animations/AnimationEffect/composite">apis/web animations/AnimationEffect/composite</a></td>
	<td class="Summary">The possible values of an animation effect's composition behavior are represented by the CompositeOperation enumeration.</td>
	<td data-sort-value="2456945.0864236" class="Modification-date">14 October 2014 14:04:27</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationEffect/iterationComposite" title="apis/web animations/AnimationEffect/iterationComposite">apis/web animations/AnimationEffect/iterationComposite</a></td>
	<td class="Summary">The iteration composite operation property of this animation effect as specified by one of the IterationCompositeOperation enumeration values.</td>
	<td data-sort-value="2456945.0838542" class="Modification-date">14 October 2014 14:00:45</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/KeyframeEffect/getFrames" title="apis/web animations/KeyframeEffect/getFrames">apis/web animations/KeyframeEffect/getFrames</a></td>
	<td class="Summary">Returns the keyframes that make up this effect as a sequence of ComputedKeyframe objects.</td>
	<td data-sort-value="2456944.4934491" class="Modification-date">13 October 2014 23:50:34</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationEffect/name" title="apis/web animations/AnimationEffect/name">apis/web animations/AnimationEffect/name</a></td>
	<td class="Summary">A string used to identify the effect.</td>
	<td data-sort-value="2456944.4893056" class="Modification-date">13 October 2014 23:44:36</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/KeyframeEffect/setFrames" title="apis/web animations/KeyframeEffect/setFrames">apis/web animations/KeyframeEffect/setFrames</a></td>
	<td class="Summary">A Keyframe object or sequence of Keyframe objects used to replace the set of keyframes that make up this effect.</td>
	<td data-sort-value="2456944.4871991" class="Modification-date">13 October 2014 23:41:34</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/KeyframeEffect" title="apis/web animations/KeyframeEffect">apis/web animations/KeyframeEffect</a></td>
	<td class="Summary">Keyframe animation effects are represented by the KeyframeEffect interface.</td>
	<td data-sort-value="2456944.4834722" class="Modification-date">13 October 2014 23:36:12</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/KeyframeEffect/constructor" title="apis/web animations/KeyframeEffect/constructor">apis/web animations/KeyframeEffect/constructor</a></td>
	<td class="Summary">Creates a new KeyframeEffect object for the given set of keyframes.</td>
	<td data-sort-value="2456944.4828588" class="Modification-date">13 October 2014 23:35:19</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingProperties/easing" title="apis/web animations/AnimationTimingProperties/easing">apis/web animations/AnimationTimingProperties/easing</a></td>
	<td class="Summary">See the easing member of the AnimationTimingReadOnly interface.
Unrecognized string values or values that correspond to a timing function that is not supported for the type of animation node to which this property is applied are treated as if the linear keyword was specified for the purpose of timing model calculations.</td>
	<td data-sort-value="2456944.4773727" class="Modification-date">13 October 2014 23:27:25</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingProperties/direction" title="apis/web animations/AnimationTimingProperties/direction">apis/web animations/AnimationTimingProperties/direction</a></td>
	<td class="Summary">See the direction member of the AnimationTimingReadOnly interface.</td>
	<td data-sort-value="2456944.4770023" class="Modification-date">13 October 2014 23:26:53</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingProperties/playbackRate" title="apis/web animations/AnimationTimingProperties/playbackRate">apis/web animations/AnimationTimingProperties/playbackRate</a></td>
	<td class="Summary">See the playbackRate member of the AnimationTimingReadOnly interface.</td>
	<td data-sort-value="2456944.4765625" class="Modification-date">13 October 2014 23:26:15</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingProperties/duration" title="apis/web animations/AnimationTimingProperties/duration">apis/web animations/AnimationTimingProperties/duration</a></td>
	<td class="Summary">See the duration member of the AnimationTimingReadOnly interface.
Real numbers less than zero, NaN values, and strings other than the lowercase value auto are treated the same as auto for the purpose of timing model calculations.</td>
	<td data-sort-value="2456944.4762963" class="Modification-date">13 October 2014 23:25:52</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingProperties/interations" title="apis/web animations/AnimationTimingProperties/interations">apis/web animations/AnimationTimingProperties/interations</a></td>
	<td class="Summary">See the iterations member of the AnimationTimingReadOnly interface.
Values less than zero and NaN values are treated as the value 1.0 for the purpose of timing model calculations.</td>
	<td data-sort-value="2456944.4758796" class="Modification-date">13 October 2014 23:25:16</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingProperties/iterationStart" title="apis/web animations/AnimationTimingProperties/iterationStart">apis/web animations/AnimationTimingProperties/iterationStart</a></td>
	<td class="Summary">See the iterationStart member of the AnimationTimingReadOnly interface.
<p>Values less than zero are clamped to zero for the purpose of timing model calculations.
</p><p>Note that the value of iterations is effectively added to the iterationStart such that an animation node with an iterationStart of ‘0.5’ and iterations of ‘2’ would still repeat twice however it would begin and end half-way through the animation node’s iteration interval.
</p>
Setting the iterationStart to a value greater than or equal to one is typically only useful in combination with an animation effect that has an iteration composite operation of ‘accumulate’.</td>
	<td data-sort-value="2456944.4754051" class="Modification-date">13 October 2014 23:24:35</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingProperties/fill" title="apis/web animations/AnimationTimingProperties/fill">apis/web animations/AnimationTimingProperties/fill</a></td>
	<td class="Summary">See the fill member of the AnimationTimingReadOnly interface.</td>
	<td data-sort-value="2456944.4750579" class="Modification-date">13 October 2014 23:24:05</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingProperties/endDelay" title="apis/web animations/AnimationTimingProperties/endDelay">apis/web animations/AnimationTimingProperties/endDelay</a></td>
	<td class="Summary">The specified end delay.
See the description of the endDelay attribute on the AnimationTiming interface.</td>
	<td data-sort-value="2456944.4745602" class="Modification-date">13 October 2014 23:23:22</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingProperties/delay" title="apis/web animations/AnimationTimingProperties/delay">apis/web animations/AnimationTimingProperties/delay</a></td>
	<td class="Summary">The specified start delay.
See the description of the delay attribute on the AnimationTiming interface.</td>
	<td data-sort-value="2456944.4740856" class="Modification-date">13 October 2014 23:22:41</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingProperties" title="apis/web animations/AnimationTimingProperties">apis/web animations/AnimationTimingProperties</a></td>
	<td class="Summary">The AnimationTimingProperties dictionary is encapsulates the timing properties of an AnimationNode so that they can be set in bulk (as in the constructor for Animation) or returned as a readonly snapshot (as in computedTiming).</td>
	<td data-sort-value="2456944.4685764" class="Modification-date">13 October 2014 23:14:45</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationNode/previousSibling" title="apis/web animations/AnimationNode/previousSibling">apis/web animations/AnimationNode/previousSibling</a></td>
	<td class="Summary">The previous sibling of this animation node.</td>
	<td data-sort-value="2456944.4668403" class="Modification-date">13 October 2014 23:12:15</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationNode/nextSibling" title="apis/web animations/AnimationNode/nextSibling">apis/web animations/AnimationNode/nextSibling</a></td>
	<td class="Summary">The next sibling of this animation node.</td>
	<td data-sort-value="2456940.6404514" class="Modification-date">10 October 2014 03:22:15</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationNode/replace" title="apis/web animations/AnimationNode/replace">apis/web animations/AnimationNode/replace</a></td>
	<td class="Summary">Replaces this AnimationNode with the passed in nodes.
<p>If there is no parent animation group, terminate these steps.
If any of the animation nodes in nodes is an inclusive ancestor of the parent animation group throw a HierarchyRequestError exception and terminate these steps.
Let reference child be the next sibling of this animation node not in nodes.
Remove this animation node from its parent animation group.
</p>
Insert nodes before reference child.</td>
	<td data-sort-value="2456940.6369676" class="Modification-date">10 October 2014 03:17:14</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationNode/after" title="apis/web animations/AnimationNode/after">apis/web animations/AnimationNode/after</a></td>
	<td class="Summary">Inserts nodes after this animation node.
<p>If there is no parent animation group, terminate these steps.
If any of the animation nodes in nodes is an inclusive ancestor of this animation node throw a HierarchyRequestError exception and terminate these steps.
Let reference child be the next sibling of this animation node not in nodes.
</p>
Insert nodes before reference child.</td>
	<td data-sort-value="2456940.6271875" class="Modification-date">10 October 2014 03:03:09</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationNode/remove" title="apis/web animations/AnimationNode/remove">apis/web animations/AnimationNode/remove</a></td>
	<td class="Summary">Removes this animation node from its parent animation group or player.</td>
	<td data-sort-value="2456940.6259606" class="Modification-date">10 October 2014 03:01:23</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationNode/before" title="apis/web animations/AnimationNode/before">apis/web animations/AnimationNode/before</a></td>
	<td class="Summary">Inserts nodes before this animation node.
<p>If there is no parent animation group, terminate these steps.
If any of the animation nodes in nodes is an inclusive ancestor of this animation node throw a HierarchyRequestError exception and terminate these steps.
Insert nodes before this animation node.
Note that this definition precludes the following usage since node is an inclusive ancestor of itself:
</p>
        node.before(node); // throws HierarchyRequestError</td>
	<td data-sort-value="2456940.6241088" class="Modification-date">10 October 2014 02:58:43</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationNode/computedTiming" title="apis/web animations/AnimationNode/computedTiming">apis/web animations/AnimationNode/computedTiming</a></td>
	<td class="Summary">Returns the calculated timing properties for this animation node. This is comparable to the computed style of an Element, window.getComputedStyle(elem).
<p>Although several of the attributes of the this object are common to the AnimationTiming object returned by the timing attribute, they have the following differences:
</p><p>duration – returns the calculated value of the iteration duration. If timing.duration is the string auto or any unsupported value, this attribute will return the current calculated value of the intrinsic iteration duration.
fill – the auto value is replaced with the specific FillMode depending on the type of animation node (see §5.8.1 The FillMode enumeration).
</p>
easing – unrecognised or unsupported values are replaced with the string linear.</td>
	<td data-sort-value="2456940.616956" class="Modification-date">10 October 2014 02:48:25</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationGroup/clone" title="apis/web animations/AnimationGroup/clone">apis/web animations/AnimationGroup/clone</a></td>
	<td class="Summary">Creates a deep copy of this AnimationGroup object using the following procedure.
<p>Let source be this AnimationGroup object, the object to be cloned.
Let cloned timing be a new AnimationTimingProperties object whose members are assigned the value of the attribute with the same name on source.timing.
Let cloned children be an empty sequence of AnimationNode objects.
For each child in source.children, append the result of calling child.clone() to cloned children.
</p>
Return a new AnimationGroup object created by calling the AnimationGroup constructor with parameters AnimationGroup(cloned children, cloned timing).</td>
	<td data-sort-value="2456940.6149421" class="Modification-date">10 October 2014 02:45:31</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationGroup/prepend" title="apis/web animations/AnimationGroup/prepend">apis/web animations/AnimationGroup/prepend</a></td>
	<td class="Summary">If any of the animation nodes in nodes is an inclusive ancestor of this animation node throw a HierarchyRequestError exception and terminate these steps.
Insert nodes before the first child.</td>
	<td data-sort-value="2456940.6128704" class="Modification-date">10 October 2014 02:42:32</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationGroup/append" title="apis/web animations/AnimationGroup/append">apis/web animations/AnimationGroup/append</a></td>
	<td class="Summary">If any of the animation nodes in nodes is an inclusive ancestor of this animation node throw a HierarchyRequestError exception and terminate these steps.
Insert nodes before null.</td>
	<td data-sort-value="2456940.612037" class="Modification-date">10 October 2014 02:41:20</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationGroup/children" title="apis/web animations/AnimationGroup/children">apis/web animations/AnimationGroup/children</a></td>
	<td class="Summary">The list of child animation nodes in the group.</td>
	<td data-sort-value="2456940.6105556" class="Modification-date">10 October 2014 02:39:12</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationGroup/lastChild" title="apis/web animations/AnimationGroup/lastChild">apis/web animations/AnimationGroup/lastChild</a></td>
	<td class="Summary">The last child of this animation group</td>
	<td data-sort-value="2456940.6100926" class="Modification-date">10 October 2014 02:38:32</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationGroup/firstChild" title="apis/web animations/AnimationGroup/firstChild">apis/web animations/AnimationGroup/firstChild</a></td>
	<td class="Summary">The first child of this animation group.</td>
	<td data-sort-value="2456940.6098148" class="Modification-date">10 October 2014 02:38:08</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationGroup/constructor" title="apis/web animations/AnimationGroup/constructor">apis/web animations/AnimationGroup/constructor</a></td>
	<td></td>
	<td data-sort-value="2456940.6040278" class="Modification-date">10 October 2014 02:29:48</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingReadOnly/easing" title="apis/web animations/AnimationTimingReadOnly/easing">apis/web animations/AnimationTimingReadOnly/easing</a></td>
	<td class="Summary">The timing function used to scale the time to produce easing effects.</td>
	<td data-sort-value="2456940.3976273" class="Modification-date">9 October 2014 21:32:35</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingReadOnly/playbackRate" title="apis/web animations/AnimationTimingReadOnly/playbackRate">apis/web animations/AnimationTimingReadOnly/playbackRate</a></td>
	<td class="Summary">The animation node’s playback rate property.</td>
	<td data-sort-value="2456940.3813657" class="Modification-date">9 October 2014 21:09:10</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingReadOnly/duration" title="apis/web animations/AnimationTimingReadOnly/duration">apis/web animations/AnimationTimingReadOnly/duration</a></td>
	<td class="Summary">The iteration duration which is a real number greater than or equal to zero (including positive infinity) representing the time taken to complete a single iteration of the animation node.</td>
	<td data-sort-value="2456940.3731944" class="Modification-date">9 October 2014 20:57:24</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingReadOnly/direction" title="apis/web animations/AnimationTimingReadOnly/direction">apis/web animations/AnimationTimingReadOnly/direction</a></td>
	<td class="Summary">The playback direction of the animation node as specified by one of the PlaybackDirection enumeration values.</td>
	<td data-sort-value="2456940.3723032" class="Modification-date">9 October 2014 20:56:07</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingReadOnly" title="apis/web animations/AnimationTimingReadOnly">apis/web animations/AnimationTimingReadOnly</a></td>
	<td class="Summary">Readonly class from which AnimationTiming classes are inherited.</td>
	<td data-sort-value="2456940.3719097" class="Modification-date">9 October 2014 20:55:33</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingReadOnly/endDelay" title="apis/web animations/AnimationTimingReadOnly/endDelay">apis/web animations/AnimationTimingReadOnly/endDelay</a></td>
	<td class="Summary">The end delay which represents the number of milliseconds from the end of an animation node’s active interval until the start time of any animation node that may follow, for example, in an animation sequence.</td>
	<td data-sort-value="2456940.3656134" class="Modification-date">9 October 2014 20:46:29</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingReadOnly/iterations" title="apis/web animations/AnimationTimingReadOnly/iterations">apis/web animations/AnimationTimingReadOnly/iterations</a></td>
	<td class="Summary">The animation node’s iteration count property.
A real number greater than or equal to zero (including positive infinity) representing the number of times to repeat the animation node.</td>
	<td data-sort-value="2456940.3649421" class="Modification-date">9 October 2014 20:45:31</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingReadOnly/iterationStart" title="apis/web animations/AnimationTimingReadOnly/iterationStart">apis/web animations/AnimationTimingReadOnly/iterationStart</a></td>
	<td class="Summary">The animation node’s iteration start property.
A finite real number greater than or equal to zero representing the number of iterations into the animation node at which to begin.</td>
	<td data-sort-value="2456940.3606366" class="Modification-date">9 October 2014 20:39:19</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingReadOnly/fill" title="apis/web animations/AnimationTimingReadOnly/fill">apis/web animations/AnimationTimingReadOnly/fill</a></td>
	<td class="Summary">The fill mode as specified by one of the FillMode enumeration values.
<p>When performing timing calculations the special value auto is expanded to one of the fill modes recognized by the timing model as follows,
</p><p>If the animation node to which the fill mode is being is applied is an animation,
Use none as the fill mode.
Otherwise,
</p>
Use both as the fill mode.</td>
	<td data-sort-value="2456940.3591551" class="Modification-date">9 October 2014 20:37:11</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimingReadOnly/delay" title="apis/web animations/AnimationTimingReadOnly/delay">apis/web animations/AnimationTimingReadOnly/delay</a></td>
	<td class="Summary">The start delay which represents the number of milliseconds from an animation node’s start time to the start of the active interval.</td>
	<td data-sort-value="2456940.3559375" class="Modification-date">9 October 2014 20:32:33</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/playState" title="apis/web animations/AnimationPlayer/playState">apis/web animations/AnimationPlayer/playState</a></td>
	<td class="Summary">The play state of this player.</td>
	<td data-sort-value="2456939.4571759" class="Modification-date">8 October 2014 22:58:20</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer" title="apis/web animations/AnimationPlayer">apis/web animations/AnimationPlayer</a></td>
	<td class="Summary">Represents a single animation player. Players connect animation node, or source, to a timeline and provides playback controls.</td>
	<td data-sort-value="2456939.4536574" class="Modification-date">8 October 2014 22:53:16</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/AnimationPlayState" title="apis/web animations/AnimationPlayer/AnimationPlayState">apis/web animations/AnimationPlayer/AnimationPlayState</a></td>
	<td class="Summary">An enumeration of the various AnimationPlayer states.</td>
	<td data-sort-value="2456939.4515278" class="Modification-date">8 October 2014 22:50:12</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/reverse" title="apis/web animations/AnimationPlayer/reverse">apis/web animations/AnimationPlayer/reverse</a></td>
	<td class="Summary">Inverts the playback rate of this player and seeks to the start of the source content if if has finished playing in the reversed direction using the reverse a player procedure for this object.</td>
	<td data-sort-value="2456939.4427546" class="Modification-date">8 October 2014 22:37:34</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/pause" title="apis/web animations/AnimationPlayer/pause">apis/web animations/AnimationPlayer/pause</a></td>
	<td class="Summary">Suspends the playback of this player by running the procedure to pause a player for this object.</td>
	<td data-sort-value="2456939.4418634" class="Modification-date">8 October 2014 22:36:17</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/play" title="apis/web animations/AnimationPlayer/play">apis/web animations/AnimationPlayer/play</a></td>
	<td class="Summary">Unpauses the player and rewinds if it has finished playing using the procedure to play a player for this object.</td>
	<td data-sort-value="2456939.4413542" class="Modification-date">8 October 2014 22:35:33</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/finish" title="apis/web animations/AnimationPlayer/finish">apis/web animations/AnimationPlayer/finish</a></td>
	<td class="Summary">Seeks the player to the end of the source content in the current direction by running the finish a player procedure for this object.</td>
	<td data-sort-value="2456939.4405556" class="Modification-date">8 October 2014 22:34:24</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/cancel" title="apis/web animations/AnimationPlayer/cancel">apis/web animations/AnimationPlayer/cancel</a></td>
	<td class="Summary">Clears all effects caused by this player and aborts its playback by running the cancel a player procedure for this object.</td>
	<td data-sort-value="2456939.438912" class="Modification-date">8 October 2014 22:32:02</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/finished" title="apis/web animations/AnimationPlayer/finished">apis/web animations/AnimationPlayer/finished</a></td>
	<td class="Summary">Returns the current finished promise for this object.</td>
	<td data-sort-value="2456939.4380556" class="Modification-date">8 October 2014 22:30:48</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/ready" title="apis/web animations/AnimationPlayer/ready">apis/web animations/AnimationPlayer/ready</a></td>
	<td class="Summary">Returns the current ready promise for this object.</td>
	<td data-sort-value="2456939.4347454" class="Modification-date">8 October 2014 22:26:02</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/source" title="apis/web animations/AnimationPlayer/source">apis/web animations/AnimationPlayer/source</a></td>
	<td class="Summary">The source content associated with this player. Setting this attribute updates the object’s source content using the procedure to set the source content of a player.</td>
	<td data-sort-value="2456939.4292477" class="Modification-date">8 October 2014 22:18:07</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/timeline" title="apis/web animations/AnimationPlayer/timeline">apis/web animations/AnimationPlayer/timeline</a></td>
	<td class="Summary">The timeline associated with this player. Setting this attribute updates the object’s timeline using the procedure to set the timeline of a player.</td>
	<td data-sort-value="2456939.423044" class="Modification-date">8 October 2014 22:09:11</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/playbackRate" title="apis/web animations/AnimationPlayer/playbackRate">apis/web animations/AnimationPlayer/playbackRate</a></td>
	<td class="Summary">The playback rate of this player. Setting this attribute follows the procedure to update the player playback rate of this object to the new value.</td>
	<td data-sort-value="2456939.4201389" class="Modification-date">8 October 2014 22:05:00</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/currentTime" title="apis/web animations/AnimationPlayer/currentTime">apis/web animations/AnimationPlayer/currentTime</a></td>
	<td class="Summary">The current time of this player unless this player has a pending pause task, in which case this attribute returns null.</td>
	<td data-sort-value="2456939.416956" class="Modification-date">8 October 2014 22:00:25</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/startTime" title="apis/web animations/AnimationPlayer/startTime">apis/web animations/AnimationPlayer/startTime</a></td>
	<td class="Summary">Returns the start time of this player. Setting this attribute updates the player start time using the procedure to update the player start time of this object to the new value.</td>
	<td data-sort-value="2456939.4154398" class="Modification-date">8 October 2014 21:58:14</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayer/constructor" title="apis/web animations/AnimationPlayer/constructor">apis/web animations/AnimationPlayer/constructor</a></td>
	<td class="Summary">Constructs an new AnimationPlayer object.</td>
	<td data-sort-value="2456939.4125579" class="Modification-date">8 October 2014 21:54:05</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimeline/play" title="apis/web animations/AnimationTimeline/play">apis/web animations/AnimationTimeline/play</a></td>
	<td class="Summary">Creates a new <a href="/wiki/apis/web_animations/AnimationPlayer" title="apis/web animations/AnimationPlayer"><b>AnimationPlayer</b></a> object associated with this timeline that begins playback as soon as it is ready.</td>
	<td data-sort-value="2456939.4084375" class="Modification-date">8 October 2014 21:48:09</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/Animation/constructor" title="apis/web animations/Animation/constructor">apis/web animations/Animation/constructor</a></td>
	<td></td>
	<td data-sort-value="2456938.9307986" class="Modification-date">8 October 2014 10:20:21</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimeline/getAnimationPlayers" title="apis/web animations/AnimationTimeline/getAnimationPlayers">apis/web animations/AnimationTimeline/getAnimationPlayers</a></td>
	<td class="Summary">Returns the set of <a href="/wiki/apis/web_animations/AnimationPlayer" title="apis/web animations/AnimationPlayer"><b>Animation Player</b></a> objects associated with this timeline that have associated source content which is current or in effect.</td>
	<td data-sort-value="2456938.900706" class="Modification-date">8 October 2014 09:37:01</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimeline/currentTime" title="apis/web animations/AnimationTimeline/currentTime">apis/web animations/AnimationTimeline/currentTime</a></td>
	<td class="Summary">Returns the time value for this timeline or null if this timeline is inactive.</td>
	<td data-sort-value="2456938.8975347" class="Modification-date">8 October 2014 09:32:27</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationEffect/clone" title="apis/web animations/AnimationEffect/clone">apis/web animations/AnimationEffect/clone</a></td>
	<td class="Summary">Creates and returns a new object of the same type as this object's most-derived interface such that it will produce the same output as this object.</td>
	<td data-sort-value="2456938.8670949" class="Modification-date">8 October 2014 08:48:37</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/MotionPathEffect/MotionPathEffectOptions" title="apis/web animations/MotionPathEffect/MotionPathEffectOptions">apis/web animations/MotionPathEffect/MotionPathEffectOptions</a></td>
	<td></td>
	<td data-sort-value="2456938.8603704" class="Modification-date">8 October 2014 08:38:56</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationPlayerEvent" title="apis/web animations/AnimationPlayerEvent">apis/web animations/AnimationPlayerEvent</a></td>
	<td class="Summary">Constructs a new AnimationPlayerEvent object as described in Constructing events in [DOM4].
<a rel="nofollow" class="external free" href="http://www.w3.org/TR/dom/#constructing-events">http://www.w3.org/TR/dom/#constructing-events</a></td>
	<td data-sort-value="2456938.842963" class="Modification-date">8 October 2014 08:13:52</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/MotionPathEffect" title="apis/web animations/MotionPathEffect">apis/web animations/MotionPathEffect</a></td>
	<td class="Summary">Motion path animation effects are represented by the MotionPathEffect interface.</td>
	<td data-sort-value="2456938.84125" class="Modification-date">8 October 2014 08:11:24</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationEffectapis/web_animations/AnimationEffect/CompositeOperation" title="apis/web animations/AnimationEffectapis/web animations/AnimationEffect/CompositeOperation">apis/web animations/AnimationEffectapis/web animations/AnimationEffect/CompositeOperation</a></td>
	<td></td>
	<td data-sort-value="2456938.5097569" class="Modification-date">8 October 2014 00:14:03</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationEffect/CompositeOperation" title="apis/web animations/AnimationEffect/CompositeOperation">apis/web animations/AnimationEffect/CompositeOperation</a></td>
	<td class="Summary">The possible values of an animation effect's composition behavior are represented by the CompositeOperation enumeration.</td>
	<td data-sort-value="2456938.5056713" class="Modification-date">8 October 2014 00:08:10</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTiming" title="apis/web animations/AnimationTiming">apis/web animations/AnimationTiming</a></td>
	<td class="Summary">Timing parameters for an AnimationNode are collected together under the AnimationTiming type.</td>
	<td data-sort-value="2456938.4917477" class="Modification-date">7 October 2014 23:48:07</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationNode/parent" title="apis/web animations/AnimationNode/parent">apis/web animations/AnimationNode/parent</a></td>
	<td class="Summary">The parent animation group of this animation node or null if this animation node does not have a parent animation group.</td>
	<td data-sort-value="2456938.4869907" class="Modification-date">7 October 2014 23:41:16</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationNode/timing" title="apis/web animations/AnimationNode/timing">apis/web animations/AnimationNode/timing</a></td>
	<td class="Summary">Returns the input timing properties specified for this animation node. This is comparable to the specified style on an Element, elem.style.</td>
	<td data-sort-value="2456938.4844329" class="Modification-date">7 October 2014 23:37:35</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationGroup" title="apis/web animations/AnimationGroup">apis/web animations/AnimationGroup</a></td>
	<td class="Summary">Animation groups are represented by the AnimationGroup interface.</td>
	<td data-sort-value="2456938.4817014" class="Modification-date">7 October 2014 23:33:39</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationSequence" title="apis/web animations/AnimationSequence">apis/web animations/AnimationSequence</a></td>
	<td class="Summary">Animation sequences are represented by the AnimationSequence interface.</td>
	<td data-sort-value="2456938.4803472" class="Modification-date">7 October 2014 23:31:42</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/Animation/target" title="apis/web animations/Animation/target">apis/web animations/Animation/target</a></td>
	<td></td>
	<td data-sort-value="2456938.4578704" class="Modification-date">7 October 2014 22:59:20</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/Animation/effect" title="apis/web animations/Animation/effect">apis/web animations/Animation/effect</a></td>
	<td></td>
	<td data-sort-value="2456938.4456481" class="Modification-date">7 October 2014 22:41:44</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationNode" title="apis/web animations/AnimationNode">apis/web animations/AnimationNode</a></td>
	<td class="Summary">Animation nodes are represented in the Web Animations API by the AnimationNode interface.</td>
	<td data-sort-value="2456938.3998032" class="Modification-date">7 October 2014 21:35:43</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/CompositeOperation" title="apis/web animations/CompositeOperation">apis/web animations/CompositeOperation</a></td>
	<td class="Summary">The possible values of an animation effect’s composition behavior are represented by the CompositeOperation enumeration.</td>
	<td data-sort-value="2456938.3894097" class="Modification-date">7 October 2014 21:20:45</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/IterationCompositeOperation" title="apis/web animations/IterationCompositeOperation">apis/web animations/IterationCompositeOperation</a></td>
	<td class="Summary">The possible values of an animation effect’s iteration composite operation are represented by the IterationCompositeOperation enumeration.</td>
	<td data-sort-value="2456938.3883796" class="Modification-date">7 October 2014 21:19:16</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationNodeList" title="apis/web animations/AnimationNodeList">apis/web animations/AnimationNodeList</a></td>
	<td class="Summary">The sole reason this interface exists is to provide a familiar experience for authors familiar with DOM interfaces where child nodes are accessed via a children member.</td>
	<td data-sort-value="2456938.3839815" class="Modification-date">7 October 2014 21:12:56</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/web_animations/ComputedTimingProperties" title="apis/web animations/ComputedTimingProperties">apis/web animations/ComputedTimingProperties</a></td>
	<td></td>
	<td data-sort-value="2456938.3804514" class="Modification-date">7 October 2014 21:07:51</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/web_animations/AnimationTimeline" title="apis/web animations/AnimationTimeline">apis/web animations/AnimationTimeline</a></td>
	<td class="Summary">Representation of a timeline, including the document timeline.</td>
	<td data-sort-value="2456938.0680671" class="Modification-date">7 October 2014 13:38:01</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/audio-video/audio" title="apis/audio-video/audio">apis/audio-video/audio</a></td>
	<td class="Summary">The audio object is part of the HTML5 audio api. It extends the &lt;audio&gt; tag and allows users to access audio data. This enables the ability to manipulate or create new audio data.</td>
	<td data-sort-value="2456924.2050694" class="Modification-date">23 September 2014 16:55:18</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/audio-video/track" title="apis/audio-video/track">apis/audio-video/track</a></td>
	<td></td>
	<td data-sort-value="2456924.2027431" class="Modification-date">23 September 2014 16:51:57</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/battery_status/BatteryManager/charging" title="apis/battery status/BatteryManager/charging">apis/battery status/BatteryManager/charging</a></td>
	<td class="Summary">Represents if the system's battery is charging.</td>
	<td data-sort-value="2456924.1962731" class="Modification-date">23 September 2014 16:42:38</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/battery_status/BatteryManager/chargingTime" title="apis/battery status/BatteryManager/chargingTime">apis/battery status/BatteryManager/chargingTime</a></td>
	<td class="Summary">Represents the time remaining in seconds until the system's battery is fully charged.</td>
	<td data-sort-value="2456924.1959259" class="Modification-date">23 September 2014 16:42:08</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/battery_status/BatteryManager/chargingchange" title="apis/battery status/BatteryManager/chargingchange">apis/battery status/BatteryManager/chargingchange</a></td>
	<td class="Summary">Fired when the battery charging state is updated.</td>
	<td data-sort-value="2456924.1954514" class="Modification-date">23 September 2014 16:41:27</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/battery_status/BatteryManager/chargingtimechange" title="apis/battery status/BatteryManager/chargingtimechange">apis/battery status/BatteryManager/chargingtimechange</a></td>
	<td class="Summary">Fired when the battery charging time is updated.</td>
	<td data-sort-value="2456924.1950694" class="Modification-date">23 September 2014 16:40:54</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/battery_status/BatteryManager/dischargingTime" title="apis/battery status/BatteryManager/dischargingTime">apis/battery status/BatteryManager/dischargingTime</a></td>
	<td class="Summary">Represents the time remaining in seconds until the system's battery is completely discharged and the system is about to be suspended.</td>
	<td data-sort-value="2456924.1945602" class="Modification-date">23 September 2014 16:40:10</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/battery_status/BatteryManager/dischargingtimechange" title="apis/battery status/BatteryManager/dischargingtimechange">apis/battery status/BatteryManager/dischargingtimechange</a></td>
	<td class="Summary">Fired when the battery discharging time is updated.</td>
	<td data-sort-value="2456924.1941782" class="Modification-date">23 September 2014 16:39:37</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/battery_status/NavigatorBattery/battery" title="apis/battery status/NavigatorBattery/battery">apis/battery status/NavigatorBattery/battery</a></td>
	<td class="Summary">The object that exposes the battery status information.</td>
	<td data-sort-value="2456924.1926968" class="Modification-date">23 September 2014 16:37:29</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/battery_status/BatteryManager/level" title="apis/battery status/BatteryManager/level">apis/battery status/BatteryManager/level</a></td>
	<td class="Summary">Represents the current battery level scaled from 0 to 1.0.</td>
	<td data-sort-value="2456924.1923727" class="Modification-date">23 September 2014 16:37:01</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/battery_status/BatteryManager/levelchange" title="apis/battery status/BatteryManager/levelchange">apis/battery status/BatteryManager/levelchange</a></td>
	<td class="Summary">Fired when the battery level is updated.</td>
	<td data-sort-value="2456924.1920602" class="Modification-date">23 September 2014 16:36:34</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/battery_status/BatteryManager/onchargingchange" title="apis/battery status/BatteryManager/onchargingchange">apis/battery status/BatteryManager/onchargingchange</a></td>
	<td class="Summary">Handles the chargingchange event.</td>
	<td data-sort-value="2456924.1906134" class="Modification-date">23 September 2014 16:34:29</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/battery_status/BatteryManager/onchargingtimechange" title="apis/battery status/BatteryManager/onchargingtimechange">apis/battery status/BatteryManager/onchargingtimechange</a></td>
	<td class="Summary">Handles the chargingtimechange event.</td>
	<td data-sort-value="2456924.1902894" class="Modification-date">23 September 2014 16:34:01</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/battery_status/BatteryManager/ondischargingtimechange" title="apis/battery status/BatteryManager/ondischargingtimechange">apis/battery status/BatteryManager/ondischargingtimechange</a></td>
	<td class="Summary">Handles the dischargingtimechange event.</td>
	<td data-sort-value="2456924.1898727" class="Modification-date">23 September 2014 16:33:25</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/battery_status/BatteryManager/onlevelchange" title="apis/battery status/BatteryManager/onlevelchange">apis/battery status/BatteryManager/onlevelchange</a></td>
	<td class="Summary">Handles the levelchange event.</td>
	<td data-sort-value="2456924.1894329" class="Modification-date">23 September 2014 16:32:47</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/file/FileError" title="apis/file/FileError">apis/file/FileError</a></td>
	<td class="Summary">Represents an error that occurs while using the FileReader interface.
Obsolete per latest specification. Use <a href="/wiki/dom/DOMError" title="dom/DOMError">DOMError</a> instead.</td>
	<td data-sort-value="2456923.2613426" class="Modification-date">22 September 2014 18:16:20</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/file/MSStreamError" title="apis/file/MSStreamError">apis/file/MSStreamError</a></td>
	<td class="Summary">The MSStreamError object reports file-related errors asynchronously.
Obsolete per latest specification. Use <a href="/wiki/dom/DOMError" title="dom/DOMError">DOMError</a> instead.</td>
	<td data-sort-value="2456923.2552546" class="Modification-date">22 September 2014 18:07:34</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/file/MSStreamReader" title="apis/file/MSStreamReader">apis/file/MSStreamReader</a></td>
	<td class="Summary">Creates random access data (Blob) from an MSStream object.</td>
	<td data-sort-value="2456923.254838" class="Modification-date">22 September 2014 18:06:58</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/file/MSStreamReader/onabort" title="apis/file/MSStreamReader/onabort">apis/file/MSStreamReader/onabort</a></td>
	<td class="Summary">Indicates that the read has been aborted (for example, by calling <b>abort()</b>).</td>
	<td data-sort-value="2456923.2545255" class="Modification-date">22 September 2014 18:06:31</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/file/MSStreamReader/readAsBlob" title="apis/file/MSStreamReader/readAsBlob">apis/file/MSStreamReader/readAsBlob</a></td>
	<td class="Summary">Performs an asynchronous read of an <a href="/w/index.php?title=apis/file/MSStream&amp;action=edit&amp;redlink=1" class="new" title="apis/file/MSStream (page does not exist)">MSStream</a> object in order to create a <a href="/wiki/apis/file/Blob" title="apis/file/Blob">Blob</a> object.</td>
	<td data-sort-value="2456923.2536458" class="Modification-date">22 September 2014 18:05:15</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/file/MSStreamReader/readAsText" title="apis/file/MSStreamReader/readAsText">apis/file/MSStreamReader/readAsText</a></td>
	<td class="Summary">Returns partial Blob data representing the number of bytes currently loaded (as a fraction of the total), decoded into memory according to the encoding determination.</td>
	<td data-sort-value="2456923.2531597" class="Modification-date">22 September 2014 18:04:33</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/file/URL/revokeObjectURL" title="apis/file/URL/revokeObjectURL">apis/file/URL/revokeObjectURL</a></td>
	<td class="Summary">Revokes a URL from a document and frees the object associated with that URL.</td>
	<td data-sort-value="2456923.2501157" class="Modification-date">22 September 2014 18:00:10</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/image_capture/ImageCapture/getFrame" title="apis/image capture/ImageCapture/getFrame">apis/image capture/ImageCapture/getFrame</a></td>
	<td class="Summary">Gathers data from the VideoStreamTrack into a ImageData object.</td>
	<td data-sort-value="2456919.2583218" class="Modification-date">18 September 2014 18:11:59</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/image_capture/ImageCapture/onerror" title="apis/image capture/ImageCapture/onerror">apis/image capture/ImageCapture/onerror</a></td>
	<td class="Summary">Register/unregister for Image Capture error events of type ImageCaptureErrorEvent.</td>
	<td data-sort-value="2456919.2580208" class="Modification-date">18 September 2014 18:11:33</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/image_capture/ImageCapture/onframegrab" title="apis/image capture/ImageCapture/onframegrab">apis/image capture/ImageCapture/onframegrab</a></td>
	<td class="Summary">Register/unregister for frame capture events of type FrameGrabEvent.</td>
	<td data-sort-value="2456919.2577315" class="Modification-date">18 September 2014 18:11:08</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/image_capture/ImageCapture/onphoto" title="apis/image capture/ImageCapture/onphoto">apis/image capture/ImageCapture/onphoto</a></td>
	<td class="Summary">Register/unregister for photo events of type BlobEvent.</td>
	<td data-sort-value="2456919.257419" class="Modification-date">18 September 2014 18:10:41</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/image_capture/ImageCapture/onphotosettingschange" title="apis/image capture/ImageCapture/onphotosettingschange">apis/image capture/ImageCapture/onphotosettingschange</a></td>
	<td class="Summary">Register/unregister for photo settings change events of type SettingsChangeEvent.</td>
	<td data-sort-value="2456919.2570949" class="Modification-date">18 September 2014 18:10:13</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/image_capture/PhotoSettingsOptions" title="apis/image capture/PhotoSettingsOptions">apis/image capture/PhotoSettingsOptions</a></td>
	<td class="Summary">Provides the photo-specific settings options and current settings values.</td>
	<td data-sort-value="2456919.2565856" class="Modification-date">18 September 2014 18:09:29</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/image_capture/ImageCapture/photoSettingsOptions" title="apis/image capture/ImageCapture/photoSettingsOptions">apis/image capture/ImageCapture/photoSettingsOptions</a></td>
	<td class="Summary">Describes current photo settings.</td>
	<td data-sort-value="2456919.2553356" class="Modification-date">18 September 2014 18:07:41</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/image_capture/ImageCapture/setOptions" title="apis/image capture/ImageCapture/setOptions">apis/image capture/ImageCapture/setOptions</a></td>
	<td class="Summary">Applies the settings specified by the PhotoSettings object passed by parameter.</td>
	<td data-sort-value="2456919.2549537" class="Modification-date">18 September 2014 18:07:08</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/image_capture/ImageCapture/takePhoto" title="apis/image capture/ImageCapture/takePhoto">apis/image capture/ImageCapture/takePhoto</a></td>
	<td class="Summary">Gathers data from the VideoStreamTrack into a Blob containing a single still image.</td>
	<td data-sort-value="2456919.2544444" class="Modification-date">18 September 2014 18:06:24</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/image_capture/ImageCapture/videoStreamTrack" title="apis/image capture/ImageCapture/videoStreamTrack">apis/image capture/ImageCapture/videoStreamTrack</a></td>
	<td class="Summary">The MediaStream passed into the constructor.</td>
	<td data-sort-value="2456919.2540046" class="Modification-date">18 September 2014 18:05:46</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/image_capture/PhotoSettings/autoExposureMode" title="apis/image capture/PhotoSettings/autoExposureMode">apis/image capture/PhotoSettings/autoExposureMode</a></td>
	<td class="Summary">This reflects the desired auto exposure mode setting.</td>
	<td data-sort-value="2456919.2529977" class="Modification-date">18 September 2014 18:04:19</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/image_capture/PhotoSettings/autoWhiteBalanceMode" title="apis/image capture/PhotoSettings/autoWhiteBalanceMode">apis/image capture/PhotoSettings/autoWhiteBalanceMode</a></td>
	<td class="Summary">This reflects whether automatic White Balance Mode selection is desired.</td>
	<td data-sort-value="2456919.2520023" class="Modification-date">18 September 2014 18:02:53</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/image_capture/PhotoSettings/brightness" title="apis/image capture/PhotoSettings/brightness">apis/image capture/PhotoSettings/brightness</a></td>
	<td class="Summary">This reflects the desired brightness setting of the camera.</td>
	<td data-sort-value="2456919.2516667" class="Modification-date">18 September 2014 18:02:24</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/image_capture/PhotoSettings/contrast" title="apis/image capture/PhotoSettings/contrast">apis/image capture/PhotoSettings/contrast</a></td>
	<td class="Summary">This reflects the desired contrast setting of the camera.</td>
	<td data-sort-value="2456919.2513773" class="Modification-date">18 September 2014 18:01:59</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/image_capture/PhotoSettings/exposureCompensation" title="apis/image capture/PhotoSettings/exposureCompensation">apis/image capture/PhotoSettings/exposureCompensation</a></td>
	<td class="Summary">This reflects the desired exposure compensation setting.</td>
	<td data-sort-value="2456919.2510532" class="Modification-date">18 September 2014 18:01:31</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/image_capture/PhotoSettings/imageHeight" title="apis/image capture/PhotoSettings/imageHeight">apis/image capture/PhotoSettings/imageHeight</a></td>
	<td class="Summary">This reflects the desired image height.</td>
	<td data-sort-value="2456919.250706" class="Modification-date">18 September 2014 18:01:01</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/image_capture/PhotoSettings/imageWidth" title="apis/image capture/PhotoSettings/imageWidth">apis/image capture/PhotoSettings/imageWidth</a></td>
	<td class="Summary">This reflects the desired image width.</td>
	<td data-sort-value="2456919.2504051" class="Modification-date">18 September 2014 18:00:35</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/image_capture/PhotoSettings/iso" title="apis/image capture/PhotoSettings/iso">apis/image capture/PhotoSettings/iso</a></td>
	<td class="Summary">This reflects the desired camera ISO setting.</td>
	<td data-sort-value="2456919.249838" class="Modification-date">18 September 2014 17:59:46</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/image_capture/PhotoSettings/redEyeReduction" title="apis/image capture/PhotoSettings/redEyeReduction">apis/image capture/PhotoSettings/redEyeReduction</a></td>
	<td class="Summary">This reflects whether camera red eye reduction is desired.</td>
	<td data-sort-value="2456919.2495023" class="Modification-date">18 September 2014 17:59:17</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/image_capture/PhotoSettings/saturation" title="apis/image capture/PhotoSettings/saturation">apis/image capture/PhotoSettings/saturation</a></td>
	<td class="Summary">This reflects the desired saturation setting of the camera.</td>
	<td data-sort-value="2456919.2491667" class="Modification-date">18 September 2014 17:58:48</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/image_capture/PhotoSettings/whiteBalanceMode" title="apis/image capture/PhotoSettings/whiteBalanceMode">apis/image capture/PhotoSettings/whiteBalanceMode</a></td>
	<td class="Summary">This reflects the desired white balance mode setting.</td>
	<td data-sort-value="2456919.248912" class="Modification-date">18 September 2014 17:58:26</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/image_capture/PhotoSettings/sharpness" title="apis/image capture/PhotoSettings/sharpness">apis/image capture/PhotoSettings/sharpness</a></td>
	<td class="Summary">This reflects the desired sharpness setting of the camera.</td>
	<td data-sort-value="2456919.2485995" class="Modification-date">18 September 2014 17:57:59</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBCursor/delete" title="apis/indexeddb/IDBCursor/delete">apis/indexeddb/IDBCursor/delete</a></td>
	<td class="Summary">Returns an IDBRequest object and, in a separate thread, deletes the record at the cursor's position, without changing the cursor's position. Once the record is deleted, the cursor's value is set to null.</td>
	<td data-sort-value="2456918.3985532" class="Modification-date">17 September 2014 21:33:55</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBCursor/direction" title="apis/indexeddb/IDBCursor/direction">apis/indexeddb/IDBCursor/direction</a></td>
	<td class="Summary">Indicates the direction of travel within a cursor.</td>
	<td data-sort-value="2456918.3981481" class="Modification-date">17 September 2014 21:33:20</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBCursor/key" title="apis/indexeddb/IDBCursor/key">apis/indexeddb/IDBCursor/key</a></td>
	<td class="Summary">The key value for the record currently displayed by the cursor.</td>
	<td data-sort-value="2456918.3972569" class="Modification-date">17 September 2014 21:32:03</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBCursor/primaryKey" title="apis/indexeddb/IDBCursor/primaryKey">apis/indexeddb/IDBCursor/primaryKey</a></td>
	<td class="Summary">Returns the cursor's current effective key.</td>
	<td data-sort-value="2456918.3965162" class="Modification-date">17 September 2014 21:30:59</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBCursor/source" title="apis/indexeddb/IDBCursor/source">apis/indexeddb/IDBCursor/source</a></td>
	<td class="Summary">On getting, returns the IDBObjectStore or IDBIndex that the cursor is iterating. This function never returns null or throws an exception, even if the cursor is currently being iterated, has iterated past its end, or its transaction is not active.</td>
	<td data-sort-value="2456918.3960995" class="Modification-date">17 September 2014 21:30:23</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBCursor/update" title="apis/indexeddb/IDBCursor/update">apis/indexeddb/IDBCursor/update</a></td>
	<td class="Summary">Creates a structured clone of the value parameter.</td>
	<td data-sort-value="2456918.3956944" class="Modification-date">17 September 2014 21:29:48</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBCursorWithValue/value" title="apis/indexeddb/IDBCursorWithValue/value">apis/indexeddb/IDBCursorWithValue/value</a></td>
	<td></td>
	<td data-sort-value="2456918.3921875" class="Modification-date">17 September 2014 21:24:45</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBDatabase/deleteObjectStore" title="apis/indexeddb/IDBDatabase/deleteObjectStore">apis/indexeddb/IDBDatabase/deleteObjectStore</a></td>
	<td class="Summary">Destroys an object store with the given name as well as all indexes that are referencing that object store.</td>
	<td data-sort-value="2456918.3885764" class="Modification-date">17 September 2014 21:19:33</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBDatabase/name" title="apis/indexeddb/IDBDatabase/name">apis/indexeddb/IDBDatabase/name</a></td>
	<td class="Summary">Name of the connected database.</td>
	<td data-sort-value="2456918.3839468" class="Modification-date">17 September 2014 21:12:53</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBDatabase/objectStoreNames" title="apis/indexeddb/IDBDatabase/objectStoreNames">apis/indexeddb/IDBDatabase/objectStoreNames</a></td>
	<td class="Summary">Returns a list of names of the object stores currently in the connected database.</td>
	<td data-sort-value="2456918.3835764" class="Modification-date">17 September 2014 21:12:21</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBDatabaseException" title="apis/indexeddb/IDBDatabaseException">apis/indexeddb/IDBDatabaseException</a></td>
	<td class="Summary">Not supported.</td>
	<td data-sort-value="2456918.3830324" class="Modification-date">17 September 2014 21:11:34</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBDatabaseException/code" title="apis/indexeddb/IDBDatabaseException/code">apis/indexeddb/IDBDatabaseException/code</a></td>
	<td class="Summary">Not supported.</td>
	<td data-sort-value="2456918.3828356" class="Modification-date">17 September 2014 21:11:17</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBDatabaseException/message" title="apis/indexeddb/IDBDatabaseException/message">apis/indexeddb/IDBDatabaseException/message</a></td>
	<td class="Summary">Not supported.</td>
	<td data-sort-value="2456918.3826157" class="Modification-date">17 September 2014 21:10:58</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBDatabase/setVersion" title="apis/indexeddb/IDBDatabase/setVersion">apis/indexeddb/IDBDatabase/setVersion</a></td>
	<td class="Summary">Deletion candidate. Not in spec: <a rel="nofollow" class="external free" href="http://www.w3.org/TR/IndexedDB/">http://www.w3.org/TR/IndexedDB/</a></td>
	<td data-sort-value="2456918.3820602" class="Modification-date">17 September 2014 21:10:10</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBDatabase/transaction" title="apis/indexeddb/IDBDatabase/transaction">apis/indexeddb/IDBDatabase/transaction</a></td>
	<td class="Summary">Execute the steps for creating a transaction in a sychronous fashion.</td>
	<td data-sort-value="2456918.38125" class="Modification-date">17 September 2014 21:09:00</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBDatabase/version" title="apis/indexeddb/IDBDatabase/version">apis/indexeddb/IDBDatabase/version</a></td>
	<td class="Summary">Returns the version of the database when this IDBDatabaseSync instance was created.</td>
	<td data-sort-value="2456918.379456" class="Modification-date">17 September 2014 21:06:25</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBIndex/count" title="apis/indexeddb/IDBIndex/count">apis/indexeddb/IDBIndex/count</a></td>
	<td class="Summary">Runs the steps for asynchronously executing a request and returns the IDBRequest created by these steps.</td>
	<td data-sort-value="2456918.3708218" class="Modification-date">17 September 2014 20:53:59</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBIndex/get" title="apis/indexeddb/IDBIndex/get">apis/indexeddb/IDBIndex/get</a></td>
	<td class="Summary">Runs the steps for asynchronously executing a request and returns the IDBRequest created by these steps.</td>
	<td data-sort-value="2456918.3700926" class="Modification-date">17 September 2014 20:52:56</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBIndex/keyPath" title="apis/indexeddb/IDBIndex/keyPath">apis/indexeddb/IDBIndex/keyPath</a></td>
	<td class="Summary">The key path of this index. If null, this index is not auto-populated.</td>
	<td data-sort-value="2456918.3697338" class="Modification-date">17 September 2014 20:52:25</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBIndex/multiEntry" title="apis/indexeddb/IDBIndex/multiEntry">apis/indexeddb/IDBIndex/multiEntry</a></td>
	<td class="Summary">Affects how the index behaves when the result of evaluating the index's key path yields an array. If true, there is one record in the index for each item in an array of keys. If false, then there is one record for each key that is an array.</td>
	<td data-sort-value="2456918.3693403" class="Modification-date">17 September 2014 20:51:51</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBIndex/name" title="apis/indexeddb/IDBIndex/name">apis/indexeddb/IDBIndex/name</a></td>
	<td class="Summary">The name of this index.</td>
	<td data-sort-value="2456918.3690278" class="Modification-date">17 September 2014 20:51:24</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBIndex/objectStore" title="apis/indexeddb/IDBIndex/objectStore">apis/indexeddb/IDBIndex/objectStore</a></td>
	<td class="Summary">Returns a reference to the IDBObjectStore instance for the referenced object store in this IDBIndex's transaction.</td>
	<td data-sort-value="2456918.2645255" class="Modification-date">17 September 2014 18:20:55</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBIndex/openCursor" title="apis/indexeddb/IDBIndex/openCursor">apis/indexeddb/IDBIndex/openCursor</a></td>
	<td class="Summary">Creates a cursor.</td>
	<td data-sort-value="2456918.2640394" class="Modification-date">17 September 2014 18:20:13</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBIndex/openKeyCursor" title="apis/indexeddb/IDBIndex/openKeyCursor">apis/indexeddb/IDBIndex/openKeyCursor</a></td>
	<td class="Summary">Creates a cursor.</td>
	<td data-sort-value="2456918.2635069" class="Modification-date">17 September 2014 18:19:27</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBIndex/unique" title="apis/indexeddb/IDBIndex/unique">apis/indexeddb/IDBIndex/unique</a></td>
	<td class="Summary">Provides the unique flag of this index.</td>
	<td data-sort-value="2456918.2621065" class="Modification-date">17 September 2014 18:17:26</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBKeyRange/lower" title="apis/indexeddb/IDBKeyRange/lower">apis/indexeddb/IDBKeyRange/lower</a></td>
	<td class="Summary">This value is the lower-bound of the key range.</td>
	<td data-sort-value="2456918.2595255" class="Modification-date">17 September 2014 18:13:43</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBKeyRange/lowerBound" title="apis/indexeddb/IDBKeyRange/lowerBound">apis/indexeddb/IDBKeyRange/lowerBound</a></td>
	<td class="Summary">Creates and returns a new key range with lower set to lower, lowerOpen set to open, upper set to undefined and and upperOpen set to true.</td>
	<td data-sort-value="2456918.2586111" class="Modification-date">17 September 2014 18:12:24</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBKeyRange/lowerOpen" title="apis/indexeddb/IDBKeyRange/lowerOpen">apis/indexeddb/IDBKeyRange/lowerOpen</a></td>
	<td class="Summary">Returns false if the lower-bound value is included in the key range. Returns true if the lower-bound value is excluded from the key range.</td>
	<td data-sort-value="2456918.2580671" class="Modification-date">17 September 2014 18:11:37</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBKeyRange/only" title="apis/indexeddb/IDBKeyRange/only">apis/indexeddb/IDBKeyRange/only</a></td>
	<td class="Summary">Creates and returns a new key range with both lower and upper set to value and both lowerOpen and upperOpen set to false.</td>
	<td data-sort-value="2456918.2576157" class="Modification-date">17 September 2014 18:10:58</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBKeyRange/upperBound" title="apis/indexeddb/IDBKeyRange/upperBound">apis/indexeddb/IDBKeyRange/upperBound</a></td>
	<td class="Summary">Creates and returns a new key range with lower set to undefined, lowerOpen set to true, upper set to upper and and upperOpen set to open.</td>
	<td data-sort-value="2456918.2570602" class="Modification-date">17 September 2014 18:10:10</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBKeyRange/upperOpen" title="apis/indexeddb/IDBKeyRange/upperOpen">apis/indexeddb/IDBKeyRange/upperOpen</a></td>
	<td class="Summary">Returns false if the upper-bound value is included in the key range. Returns true if the upper-bound value is excluded from the key range.</td>
	<td data-sort-value="2456918.2564699" class="Modification-date">17 September 2014 18:09:19</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBObjectStore/autoIncrement" title="apis/indexeddb/IDBObjectStore/autoIncrement">apis/indexeddb/IDBObjectStore/autoIncrement</a></td>
	<td class="Summary">Provides the auto increment flag for this object store.</td>
	<td data-sort-value="2456918.2538773" class="Modification-date">17 September 2014 18:05:35</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBObjectStore/count" title="apis/indexeddb/IDBObjectStore/count">apis/indexeddb/IDBObjectStore/count</a></td>
	<td class="Summary">The count method returns the number of records in an object store.</td>
	<td data-sort-value="2456918.2527546" class="Modification-date">17 September 2014 18:03:58</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBObjectStore/openCursor" title="apis/indexeddb/IDBObjectStore/openCursor">apis/indexeddb/IDBObjectStore/openCursor</a></td>
	<td class="Summary">Creates a cursor.</td>
	<td data-sort-value="2456918.2481829" class="Modification-date">17 September 2014 17:57:23</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBObjectStore/get" title="apis/indexeddb/IDBObjectStore/get">apis/indexeddb/IDBObjectStore/get</a></td>
	<td class="Summary">Runs the steps for asynchronously executing a request and returns the IDBRequest created by these steps.</td>
	<td data-sort-value="2456918.243044" class="Modification-date">17 September 2014 17:49:59</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBObjectStore/index" title="apis/indexeddb/IDBObjectStore/index">apis/indexeddb/IDBObjectStore/index</a></td>
	<td class="Summary">Returns an IDBIndex representing an index that is part of the object store.</td>
	<td data-sort-value="2456918.2412731" class="Modification-date">17 September 2014 17:47:26</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBObjectStore/indexNames" title="apis/indexeddb/IDBObjectStore/indexNames">apis/indexeddb/IDBObjectStore/indexNames</a></td>
	<td class="Summary">Provides a list of the names of indexes on objects in this object store.</td>
	<td data-sort-value="2456918.2399306" class="Modification-date">17 September 2014 17:45:30</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBObjectStore/keyPath" title="apis/indexeddb/IDBObjectStore/keyPath">apis/indexeddb/IDBObjectStore/keyPath</a></td>
	<td class="Summary">Provides the key path of this object store.</td>
	<td data-sort-value="2456918.239456" class="Modification-date">17 September 2014 17:44:49</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBObjectStore/name" title="apis/indexeddb/IDBObjectStore/name">apis/indexeddb/IDBObjectStore/name</a></td>
	<td class="Summary">Provides the name of this object store.</td>
	<td data-sort-value="2456918.2389931" class="Modification-date">17 September 2014 17:44:09</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBObjectStore/put" title="apis/indexeddb/IDBObjectStore/put">apis/indexeddb/IDBObjectStore/put</a></td>
	<td class="Summary">Creates a structured clone of the value parameter.</td>
	<td data-sort-value="2456918.2361227" class="Modification-date">17 September 2014 17:40:01</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBObjectStore/transaction" title="apis/indexeddb/IDBObjectStore/transaction">apis/indexeddb/IDBObjectStore/transaction</a></td>
	<td class="Summary">Returns the transaction this object store belongs to.</td>
	<td data-sort-value="2456918.2313426" class="Modification-date">17 September 2014 17:33:08</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBOpenDBRequest/onUpgradeNeeded" title="apis/indexeddb/IDBOpenDBRequest/onUpgradeNeeded">apis/indexeddb/IDBOpenDBRequest/onUpgradeNeeded</a></td>
	<td class="Summary">The event handler for the upgrade needed event.</td>
	<td data-sort-value="2456918.2283333" class="Modification-date">17 September 2014 17:28:48</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBOpenDBRequest/onblocked" title="apis/indexeddb/IDBOpenDBRequest/onblocked">apis/indexeddb/IDBOpenDBRequest/onblocked</a></td>
	<td class="Summary">The event handler for the blocked event. This event is triggered when the upgradeneeded should be triggered because of a version change but the database is still in use (ie not closed) somewhere, even after the versionchange event was sent.</td>
	<td data-sort-value="2456918.2280093" class="Modification-date">17 September 2014 17:28:20</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBRequest/error" title="apis/indexeddb/IDBRequest/error">apis/indexeddb/IDBRequest/error</a></td>
	<td class="Summary">The error codes returned under certain conditions.</td>
	<td data-sort-value="2456918.2259606" class="Modification-date">17 September 2014 17:25:23</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBRequest/onerror" title="apis/indexeddb/IDBRequest/onerror">apis/indexeddb/IDBRequest/onerror</a></td>
	<td class="Summary">The event handler for the error event.</td>
	<td data-sort-value="2456918.2248958" class="Modification-date">17 September 2014 17:23:51</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBRequest/onsuccess" title="apis/indexeddb/IDBRequest/onsuccess">apis/indexeddb/IDBRequest/onsuccess</a></td>
	<td class="Summary">The event handler for the success event.</td>
	<td data-sort-value="2456918.2246065" class="Modification-date">17 September 2014 17:23:26</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBRequest/readyState" title="apis/indexeddb/IDBRequest/readyState">apis/indexeddb/IDBRequest/readyState</a></td>
	<td class="Summary">The state of the request. Every request starts in the pending state. The state changes to done when the request completes successfully or when an error occurs.</td>
	<td data-sort-value="2456918.2243287" class="Modification-date">17 September 2014 17:23:02</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBRequest/result" title="apis/indexeddb/IDBRequest/result">apis/indexeddb/IDBRequest/result</a></td>
	<td class="Summary">Returns the result of the request. If the the request failed and the result is not available, the DOMException InvalidStateError exception is thrown.</td>
	<td data-sort-value="2456918.223831" class="Modification-date">17 September 2014 17:22:19</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBTransaction/mode" title="apis/indexeddb/IDBTransaction/mode">apis/indexeddb/IDBTransaction/mode</a></td>
	<td class="Summary">The mode for isolating access to data in the object stores that are in the scope of the transaction. For possible values, see Return Value, below. The default value is readonly.</td>
	<td data-sort-value="2456918.2198264" class="Modification-date">17 September 2014 17:16:33</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBTransaction/db" title="apis/indexeddb/IDBTransaction/db">apis/indexeddb/IDBTransaction/db</a></td>
	<td class="Summary">The database connection of which this transaction is a part.</td>
	<td data-sort-value="2456918.219456" class="Modification-date">17 September 2014 17:16:01</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBTransaction/objectStore" title="apis/indexeddb/IDBTransaction/objectStore">apis/indexeddb/IDBTransaction/objectStore</a></td>
	<td class="Summary">Returns an object store that has already been added to the scope of this transaction.</td>
	<td data-sort-value="2456918.2168866" class="Modification-date">17 September 2014 17:12:19</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBTransaction/onabort" title="apis/indexeddb/IDBTransaction/onabort">apis/indexeddb/IDBTransaction/onabort</a></td>
	<td class="Summary">The event handler for the onabort event.</td>
	<td data-sort-value="2456918.2165046" class="Modification-date">17 September 2014 17:11:46</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBTransaction/oncomplete" title="apis/indexeddb/IDBTransaction/oncomplete">apis/indexeddb/IDBTransaction/oncomplete</a></td>
	<td class="Summary">The event handler for the oncomplete event.</td>
	<td data-sort-value="2456918.2162269" class="Modification-date">17 September 2014 17:11:22</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBVersionChangeEvent/newVersion" title="apis/indexeddb/IDBVersionChangeEvent/newVersion">apis/indexeddb/IDBVersionChangeEvent/newVersion</a></td>
	<td class="Summary">Returns the new version of the database, which is the version specified by the open request.</td>
	<td data-sort-value="2456918.2121759" class="Modification-date">17 September 2014 17:05:32</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBVersionChangeEvent/oldVersion" title="apis/indexeddb/IDBVersionChangeEvent/oldVersion">apis/indexeddb/IDBVersionChangeEvent/oldVersion</a></td>
	<td class="Summary">Returns the old version of the database.</td>
	<td data-sort-value="2456918.2118866" class="Modification-date">17 September 2014 17:05:07</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/indexeddb/IDBVersionChangeRequest/onblocked" title="apis/indexeddb/IDBVersionChangeRequest/onblocked">apis/indexeddb/IDBVersionChangeRequest/onblocked</a></td>
	<td class="Summary">The event handler for the blocked event.</td>
	<td data-sort-value="2456918.2095255" class="Modification-date">17 September 2014 17:01:43</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/indexeddb/indexedDB/open" title="apis/indexeddb/indexedDB/open">apis/indexeddb/indexedDB/open</a></td>
	<td class="Summary">Opens a database. See <a href="/wiki/apis/indexeddb/IDBFactory/open" title="apis/indexeddb/IDBFactory/open">apis/indexeddb/IDBFactory/open</a></td>
	<td data-sort-value="2456918.2081713" class="Modification-date">17 September 2014 16:59:46</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/internationalization/Intl/Collator" title="apis/internationalization/Intl/Collator">apis/internationalization/Intl/Collator</a></td>
	<td></td>
	<td data-sort-value="2456917.2438194" class="Modification-date">16 September 2014 17:51:06</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/internationalization/Intl/DateTimeFormat" title="apis/internationalization/Intl/DateTimeFormat">apis/internationalization/Intl/DateTimeFormat</a></td>
	<td></td>
	<td data-sort-value="2456917.2434259" class="Modification-date">16 September 2014 17:50:32</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/internationalization/Intl/NumberFormat" title="apis/internationalization/Intl/NumberFormat">apis/internationalization/Intl/NumberFormat</a></td>
	<td></td>
	<td data-sort-value="2456917.2429398" class="Modification-date">16 September 2014 17:49:50</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStream/addtrack" title="apis/media capture and streams/MediaStream/addtrack">apis/media capture and streams/MediaStream/addtrack</a></td>
	<td class="Summary">This event is fired when a track is added to the MediaStream.</td>
	<td data-sort-value="2456917.2263194" class="Modification-date">16 September 2014 17:25:54</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStream/ended" title="apis/media capture and streams/MediaStream/ended">apis/media capture and streams/MediaStream/ended</a></td>
	<td class="Summary">Is true if the MediaStream has finished, false otherwise.</td>
	<td data-sort-value="2456917.2257755" class="Modification-date">16 September 2014 17:25:07</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStream/id" title="apis/media capture and streams/MediaStream/id">apis/media capture and streams/MediaStream/id</a></td>
	<td class="Summary">A globally unique identifier string, initialized when the MediaStream object is created.</td>
	<td data-sort-value="2456917.2254861" class="Modification-date">16 September 2014 17:24:42</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStream/onaddtrack" title="apis/media capture and streams/MediaStream/onaddtrack">apis/media capture and streams/MediaStream/onaddtrack</a></td>
	<td class="Summary">Handles the addtrack event when fired on the MediaStream object.</td>
	<td data-sort-value="2456917.225162" class="Modification-date">16 September 2014 17:24:14</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStream/onended" title="apis/media capture and streams/MediaStream/onended">apis/media capture and streams/MediaStream/onended</a></td>
	<td class="Summary">Handles the ended event when fired on the MediaStream object.</td>
	<td data-sort-value="2456917.2247222" class="Modification-date">16 September 2014 17:23:36</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStream/onremovetrack" title="apis/media capture and streams/MediaStream/onremovetrack">apis/media capture and streams/MediaStream/onremovetrack</a></td>
	<td class="Summary">Handles the removetrack event when fired on the MediaStream object.</td>
	<td data-sort-value="2456917.2240741" class="Modification-date">16 September 2014 17:22:40</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStream/removetrack" title="apis/media capture and streams/MediaStream/removetrack">apis/media capture and streams/MediaStream/removetrack</a></td>
	<td class="Summary">This event is fired when a track is removed from the MediaStream.</td>
	<td data-sort-value="2456917.2235532" class="Modification-date">16 September 2014 17:21:55</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/applyConstraints" title="apis/media capture and streams/MediaStreamTrack/applyConstraints">apis/media capture and streams/MediaStreamTrack/applyConstraints</a></td>
	<td class="Summary">Replaces all existing constraints with the provided constraints, if existing constraints exist. Otherwise, it applies the newly provided constraints to the track.</td>
	<td data-sort-value="2456917.2224421" class="Modification-date">16 September 2014 17:20:19</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/capabilities" title="apis/media capture and streams/MediaStreamTrack/capabilities">apis/media capture and streams/MediaStreamTrack/capabilities</a></td>
	<td class="Summary">Returns a dictionary with all of the capabilities for the track type.</td>
	<td data-sort-value="2456917.2220833" class="Modification-date">16 September 2014 17:19:48</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/clone" title="apis/media capture and streams/MediaStreamTrack/clone">apis/media capture and streams/MediaStreamTrack/clone</a></td>
	<td class="Summary">Clones the given MediaStreamTrack.</td>
	<td data-sort-value="2456917.2216667" class="Modification-date">16 September 2014 17:19:12</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/constraints" title="apis/media capture and streams/MediaStreamTrack/constraints">apis/media capture and streams/MediaStreamTrack/constraints</a></td>
	<td class="Summary">Returns the complete constraints object associated with the track. If no mandatory constraints have been defined, the mandatory field will not be present (it will be undefined). If no optional constraints have been defined, the optional field will not be present (it will be undefined). If neither optional, nor mandatory constraints have been created, the value null is returned.</td>
	<td data-sort-value="2456917.2213194" class="Modification-date">16 September 2014 17:18:42</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/enabled" title="apis/media capture and streams/MediaStreamTrack/enabled">apis/media capture and streams/MediaStreamTrack/enabled</a></td>
	<td class="Summary">Enables the track if the new value is true, and disable it otherwise.</td>
	<td data-sort-value="2456917.2208102" class="Modification-date">16 September 2014 17:17:58</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/id" title="apis/media capture and streams/MediaStreamTrack/id">apis/media capture and streams/MediaStreamTrack/id</a></td>
	<td class="Summary">A globally unique identifier string, initialized when the MediaStreamTrack object is created.</td>
	<td data-sort-value="2456917.2205093" class="Modification-date">16 September 2014 17:17:32</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/kind" title="apis/media capture and streams/MediaStreamTrack/kind">apis/media capture and streams/MediaStreamTrack/kind</a></td>
	<td class="Summary">Returns the string "audio" if the object represents an audio track or "video" if object represents a video track.</td>
	<td data-sort-value="2456917.2200347" class="Modification-date">16 September 2014 17:16:51</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/onmute" title="apis/media capture and streams/MediaStreamTrack/onmute">apis/media capture and streams/MediaStreamTrack/onmute</a></td>
	<td class="Summary">Handles the mute event when fired on the MediaStreamTrack object.</td>
	<td data-sort-value="2456917.2045139" class="Modification-date">16 September 2014 16:54:30</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/onoverconstrained" title="apis/media capture and streams/MediaStreamTrack/onoverconstrained">apis/media capture and streams/MediaStreamTrack/onoverconstrained</a></td>
	<td class="Summary">Handles the overcontrained event when fired on the MediaStreamTrack object.</td>
	<td data-sort-value="2456917.2041551" class="Modification-date">16 September 2014 16:53:59</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/onstarted" title="apis/media capture and streams/MediaStreamTrack/onstarted">apis/media capture and streams/MediaStreamTrack/onstarted</a></td>
	<td class="Summary">Handles the started event when fired on the MediaStreamTrack object.</td>
	<td data-sort-value="2456917.2033565" class="Modification-date">16 September 2014 16:52:50</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/label" title="apis/media capture and streams/MediaStreamTrack/label">apis/media capture and streams/MediaStreamTrack/label</a></td>
	<td class="Summary">Returns the label of the object’s corresponding track, if any. If the corresponding track has or had no label, it returns the empty string.</td>
	<td data-sort-value="2456917.2025" class="Modification-date">16 September 2014 16:51:36</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/mute" title="apis/media capture and streams/MediaStreamTrack/mute">apis/media capture and streams/MediaStreamTrack/mute</a></td>
	<td class="Summary">This event fires when the MediaStreamTrack object's source is temporarily unable to provide data.</td>
	<td data-sort-value="2456917.2021759" class="Modification-date">16 September 2014 16:51:08</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/muted" title="apis/media capture and streams/MediaStreamTrack/muted">apis/media capture and streams/MediaStreamTrack/muted</a></td>
	<td class="Summary">Returns true if the track is muted, and false otherwise.</td>
	<td data-sort-value="2456917.2017593" class="Modification-date">16 September 2014 16:50:32</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/onended" title="apis/media capture and streams/MediaStreamTrack/onended">apis/media capture and streams/MediaStreamTrack/onended</a></td>
	<td class="Summary">Handles the ended event when fired on the MediaStreamTrack object.</td>
	<td data-sort-value="2456917.2012616" class="Modification-date">16 September 2014 16:49:49</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/onunmute" title="apis/media capture and streams/MediaStreamTrack/onunmute">apis/media capture and streams/MediaStreamTrack/onunmute</a></td>
	<td class="Summary">Handles the unmute event when fired on the MediaStreamTrack object.</td>
	<td data-sort-value="2456917.2008565" class="Modification-date">16 September 2014 16:49:14</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/overconstrained" title="apis/media capture and streams/MediaStreamTrack/overconstrained">apis/media capture and streams/MediaStreamTrack/overconstrained</a></td>
	<td class="Summary">This event fires asynchronously for each affected track (when multiple tracks share the same source) after the user agent has evaluated the current constraints against a given sourceId and is not able to configure the source within the limitations established by the union of imposed constraints.</td>
	<td data-sort-value="2456917.2004861" class="Modification-date">16 September 2014 16:48:42</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/readonly" title="apis/media capture and streams/MediaStreamTrack/readonly">apis/media capture and streams/MediaStreamTrack/readonly</a></td>
	<td class="Summary">Returns true If the track (audio or video) is backed by a read-only source such as a file, or the track source is a local microphone or camera, but is shared so that this track cannot modify any of the source's settings. Returns false otherwise.</td>
	<td data-sort-value="2456917.2001505" class="Modification-date">16 September 2014 16:48:13</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/readyState" title="apis/media capture and streams/MediaStreamTrack/readyState">apis/media capture and streams/MediaStreamTrack/readyState</a></td>
	<td class="Summary">Returns the state of the track.</td>
	<td data-sort-value="2456917.1997569" class="Modification-date">16 September 2014 16:47:39</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/remote" title="apis/media capture and streams/MediaStreamTrack/remote">apis/media capture and streams/MediaStreamTrack/remote</a></td>
	<td class="Summary">Returns true if the track is sourced by an RTCPeerConnection. Returns false otherwise.</td>
	<td data-sort-value="2456917.1991667" class="Modification-date">16 September 2014 16:46:48</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/started" title="apis/media capture and streams/MediaStreamTrack/started">apis/media capture and streams/MediaStreamTrack/started</a></td>
	<td class="Summary">This event fires when the MediaStreamTrack object has just transitioned from the "new" readyState to another state.</td>
	<td data-sort-value="2456917.1987847" class="Modification-date">16 September 2014 16:46:15</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/states" title="apis/media capture and streams/MediaStreamTrack/states">apis/media capture and streams/MediaStreamTrack/states</a></td>
	<td class="Summary">Returns an object containing all the state variables associated with the allowed constraints.</td>
	<td data-sort-value="2456917.1983333" class="Modification-date">16 September 2014 16:45:36</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/stop" title="apis/media capture and streams/MediaStreamTrack/stop">apis/media capture and streams/MediaStreamTrack/stop</a></td>
	<td class="Summary">Permanently stop the generation of data for track's source.</td>
	<td data-sort-value="2456917.1978472" class="Modification-date">16 September 2014 16:44:54</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/MediaStreamTrack/unmute" title="apis/media capture and streams/MediaStreamTrack/unmute">apis/media capture and streams/MediaStreamTrack/unmute</a></td>
	<td class="Summary">This event fires when the MediaStreamTrack object's source is live again after having been temporarily unable to provide data.</td>
	<td data-sort-value="2456917.1969792" class="Modification-date">16 September 2014 16:43:39</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_capture_and_streams/ended" title="apis/media capture and streams/ended">apis/media capture and streams/ended</a></td>
	<td class="Summary">This event is fired when a MediaStream is stopped.</td>
	<td data-sort-value="2456917.1962731" class="Modification-date">16 September 2014 16:42:38</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_recorder/MediaRecorder" title="apis/media recorder/MediaRecorder">apis/media recorder/MediaRecorder</a></td>
	<td></td>
	<td data-sort-value="2456916.350162" class="Modification-date">15 September 2014 20:24:14</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_source_extensions/MediaSource/endOfStream" title="apis/media source extensions/MediaSource/endOfStream">apis/media source extensions/MediaSource/endOfStream</a></td>
	<td class="Summary">Used to indicate that the end of the stream has been reached.</td>
	<td data-sort-value="2456916.3454514" class="Modification-date">15 September 2014 20:17:27</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/media_source_extensions/VideoPlaybackQuality/creationTime" title="apis/media source extensions/VideoPlaybackQuality/creationTime">apis/media source extensions/VideoPlaybackQuality/creationTime</a></td>
	<td class="Summary">Gets the timestamp for when the VideoPlaybackQuality metrics were collected.</td>
	<td data-sort-value="2456916.34375" class="Modification-date">15 September 2014 20:15:00</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/media_source_extensions/VideoPlaybackQuality/droppedVideoFrames" title="apis/media source extensions/VideoPlaybackQuality/droppedVideoFrames">apis/media source extensions/VideoPlaybackQuality/droppedVideoFrames</a></td>
	<td class="Summary">Gets the number of dropped video frames.</td>
	<td data-sort-value="2456916.3433565" class="Modification-date">15 September 2014 20:14:26</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/localDescription" title="apis/webrtc/RTCPeerConnection/localDescription">apis/webrtc/RTCPeerConnection/localDescription</a></td>
	<td class="Summary">Returns the <a href="/wiki/apis/webrtc/RTCSessionDescription" title="apis/webrtc/RTCSessionDescription">RTCSessionDescription</a> most recently passed to the <a href="/wiki/apis/webrtc/RTCPeerConnection/setLocalDescription" title="apis/webrtc/RTCPeerConnection/setLocalDescription">setLocalDescription()</a> method along with any local candidate descriptions generated since the method was called.</td>
	<td data-sort-value="2456916.3339699" class="Modification-date">15 September 2014 20:00:55</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/localStreams" title="apis/webrtc/RTCPeerConnection/localStreams">apis/webrtc/RTCPeerConnection/localStreams</a></td>
	<td class="Summary">Returns an array of <a href="/wiki/apis/webrtc/MediaStream" title="apis/webrtc/MediaStream">MediaStream</a> objects added to the connection with <a href="/wiki/apis/webrtc/RTCPeerConnection/addStream" title="apis/webrtc/RTCPeerConnection/addStream">addStream()</a>.</td>
	<td data-sort-value="2456916.3336574" class="Modification-date">15 September 2014 20:00:28</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/negotiationneeded" title="apis/webrtc/RTCPeerConnection/negotiationneeded">apis/webrtc/RTCPeerConnection/negotiationneeded</a></td>
	<td class="Summary">The browser anticipates a session negotiation is required.
It is triggered whenever <a href="/wiki/apis/webrtc/RTCPeerConnection/addStream" title="apis/webrtc/RTCPeerConnection/addStream">addStream</a>, <a href="/wiki/apis/webrtc/RTCPeerConnection/removeStream" title="apis/webrtc/RTCPeerConnection/removeStream">removeStream</a> or <a href="/wiki/apis/webrtc/RTCPeerConnection/setIdentityProvider" title="apis/webrtc/RTCPeerConnection/setIdentityProvider">setIdentityProvider</a> methods were called successfully and <a href="/wiki/apis/webrtc/RTCPeerConnection" title="apis/webrtc/RTCPeerConnection">RTCPeerConnection</a> signalingState is <code>stable</code> .</td>
	<td data-sort-value="2456916.333206" class="Modification-date">15 September 2014 19:59:49</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/onaddstream" title="apis/webrtc/RTCPeerConnection/onaddstream">apis/webrtc/RTCPeerConnection/onaddstream</a></td>
	<td class="Summary">Handles the <a href="/w/index.php?title=apis/webrtc/RTCPeerConnection/addstream&amp;action=edit&amp;redlink=1" class="new" title="apis/webrtc/RTCPeerConnection/addstream (page does not exist)">addstream</a> event fired when <a href="/wiki/apis/webrtc/RTCPeerConnection/setRemoteDescription" title="apis/webrtc/RTCPeerConnection/setRemoteDescription">setRemoteDescription()</a> is called.</td>
	<td data-sort-value="2456916.3215972" class="Modification-date">15 September 2014 19:43:06</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/ondatachannel" title="apis/webrtc/RTCPeerConnection/ondatachannel">apis/webrtc/RTCPeerConnection/ondatachannel</a></td>
	<td class="Summary">Handles the <b>datachannel</b> event.</td>
	<td data-sort-value="2456916.32125" class="Modification-date">15 September 2014 19:42:36</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/ongatheringchange" title="apis/webrtc/RTCPeerConnection/ongatheringchange">apis/webrtc/RTCPeerConnection/ongatheringchange</a></td>
	<td class="Summary">Handles the <b>gatheringchange</b> event for a change to the <a href="/wiki/apis/webrtc/RTCPeerConnection/iceGatheringState" title="apis/webrtc/RTCPeerConnection/iceGatheringState">iceGatheringState</a> property.</td>
	<td data-sort-value="2456916.3207639" class="Modification-date">15 September 2014 19:41:54</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/onicecandidate" title="apis/webrtc/RTCPeerConnection/onicecandidate">apis/webrtc/RTCPeerConnection/onicecandidate</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/icechange" title="apis/webrtc/RTCPeerConnection/icechange">icechange</a> event for a change to the <a href="/wiki/apis/webrtc/RTCPeerConnection/iceState" title="apis/webrtc/RTCPeerConnection/iceState">apis/webrtc/RTCPeerConnection/iceState</a> property. It is called any time there is a new ICE candidate added to a previous offer or answer.</td>
	<td data-sort-value="2456916.3196296" class="Modification-date">15 September 2014 19:40:16</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/onicechange" title="apis/webrtc/RTCPeerConnection/onicechange">apis/webrtc/RTCPeerConnection/onicechange</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/icechange" title="apis/webrtc/RTCPeerConnection/icechange">icechange</a> event. It is called any time the <a href="/wiki/apis/webrtc/RTCPeerConnection/iceState" title="apis/webrtc/RTCPeerConnection/iceState">iceState</a>  changes.</td>
	<td data-sort-value="2456916.3192708" class="Modification-date">15 September 2014 19:39:45</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/onidentityresult" title="apis/webrtc/RTCPeerConnection/onidentityresult">apis/webrtc/RTCPeerConnection/onidentityresult</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/identityresult" title="apis/webrtc/RTCPeerConnection/identityresult">identityresult</a> event for the success or failure of an identity verification.</td>
	<td data-sort-value="2456916.3187963" class="Modification-date">15 September 2014 19:39:04</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/onnegotiationneeded" title="apis/webrtc/RTCPeerConnection/onnegotiationneeded">apis/webrtc/RTCPeerConnection/onnegotiationneeded</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/negotiationneeded" title="apis/webrtc/RTCPeerConnection/negotiationneeded">negotiationneeded</a> event.</td>
	<td data-sort-value="2456916.3180787" class="Modification-date">15 September 2014 19:38:02</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/onopen" title="apis/webrtc/RTCPeerConnection/onopen">apis/webrtc/RTCPeerConnection/onopen</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/open" title="apis/webrtc/RTCPeerConnection/open">open</a> event.
Testing.</td>
	<td data-sort-value="2456916.3058449" class="Modification-date">15 September 2014 19:20:25</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/onstatechange" title="apis/webrtc/RTCPeerConnection/onstatechange">apis/webrtc/RTCPeerConnection/onstatechange</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/statechange" title="apis/webrtc/RTCPeerConnection/statechange">statechange</a> event for when the <a href="/wiki/apis/webrtc/RTCPeerConnection/readyState" title="apis/webrtc/RTCPeerConnection/readyState">readyState</a> property is changed, i.e. with a call to <a href="/wiki/apis/webrtc/RTCPeerConnection/setLocalDescription" title="apis/webrtc/RTCPeerConnection/setLocalDescription">setLocalDescription()</a> or <a href="/wiki/apis/webrtc/RTCPeerConnection/setRemoteDescription" title="apis/webrtc/RTCPeerConnection/setRemoteDescription">setRemoteDescription()</a>. The event does not fire when a new RTCPeerConnection object is created.</td>
	<td data-sort-value="2456916.3001273" class="Modification-date">15 September 2014 19:12:11</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/open" title="apis/webrtc/RTCPeerConnection/open">apis/webrtc/RTCPeerConnection/open</a></td>
	<td></td>
	<td data-sort-value="2456913.2715972" class="Modification-date">12 September 2014 18:31:06</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/readyState" title="apis/webrtc/RTCPeerConnection/readyState">apis/webrtc/RTCPeerConnection/readyState</a></td>
	<td class="Summary">Returns the ready state of the peer connection.</td>
	<td data-sort-value="2456913.2704398" class="Modification-date">12 September 2014 18:29:26</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/remoteDescription" title="apis/webrtc/RTCPeerConnection/remoteDescription">apis/webrtc/RTCPeerConnection/remoteDescription</a></td>
	<td class="Summary">Returns the <a href="/wiki/apis/webrtc/RTCSessionDescription" title="apis/webrtc/RTCSessionDescription">RTCSessionDescription</a> most recently passed to the <a href="/wiki/apis/webrtc/RTCPeerConnection/setRemoteDescription" title="apis/webrtc/RTCPeerConnection/setRemoteDescription">setRemoteDescription()</a> method along with any remote candidate descriptions supplied with <a href="/wiki/apis/webrtc/RTCPeerConnection/addIceCandidate" title="apis/webrtc/RTCPeerConnection/addIceCandidate">addIceCandidate()</a>. Returns null if the remote description has not been set.</td>
	<td data-sort-value="2456913.2701273" class="Modification-date">12 September 2014 18:28:59</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/remoteStreams" title="apis/webrtc/RTCPeerConnection/remoteStreams">apis/webrtc/RTCPeerConnection/remoteStreams</a></td>
	<td class="Summary">Returns an array of <a href="/wiki/apis/webrtc/MediaStream" title="apis/webrtc/MediaStream">MediaStream</a> objects added to the connection by the remote peer. This array is updated when the <a href="/wiki/apis/webrtc/RTCPeerConnection/onaddstream" title="apis/webrtc/RTCPeerConnection/onaddstream">addstream</a> and <a href="/wiki/apis/webrtc/RTCPeerConnection/removeStream" title="apis/webrtc/RTCPeerConnection/removeStream">removestream</a> events are fired.</td>
	<td data-sort-value="2456913.2695255" class="Modification-date">12 September 2014 18:28:07</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/removeStream" title="apis/webrtc/RTCPeerConnection/removeStream">apis/webrtc/RTCPeerConnection/removeStream</a></td>
	<td class="Summary">Removes the given stream from the <a href="/wiki/apis/webrtc/RTCPeerConnection/localStreams" title="apis/webrtc/RTCPeerConnection/localStreams">localStreams</a> array in the RTCPeerConnection and fires the <a href="/wiki/apis/webrtc/RTCPeerConnection/negotiationneeded" title="apis/webrtc/RTCPeerConnection/negotiationneeded">negotiationneeded</a> event.</td>
	<td data-sort-value="2456913.2678704" class="Modification-date">12 September 2014 18:25:44</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/setIdentityProvider" title="apis/webrtc/RTCPeerConnection/setIdentityProvider">apis/webrtc/RTCPeerConnection/setIdentityProvider</a></td>
	<td class="Summary">Sets the identity provider. Not required if the browser is already configured for an identity provider.</td>
	<td data-sort-value="2456913.2661458" class="Modification-date">12 September 2014 18:23:15</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/setLocalDescription" title="apis/webrtc/RTCPeerConnection/setLocalDescription">apis/webrtc/RTCPeerConnection/setLocalDescription</a></td>
	<td class="Summary">Applies the supplied <a href="/wiki/apis/webrtc/RTCSessionDescription" title="apis/webrtc/RTCSessionDescription">RTCSessionDescription</a> to the local description.</td>
	<td data-sort-value="2456913.2655208" class="Modification-date">12 September 2014 18:22:21</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/setRemoteDescription" title="apis/webrtc/RTCPeerConnection/setRemoteDescription">apis/webrtc/RTCPeerConnection/setRemoteDescription</a></td>
	<td class="Summary">Applies the supplied <a href="/wiki/apis/webrtc/RTCSessionDescription" title="apis/webrtc/RTCSessionDescription">RTCSessionDescription</a> to the remote description.</td>
	<td data-sort-value="2456913.2650463" class="Modification-date">12 September 2014 18:21:40</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/statechange" title="apis/webrtc/RTCPeerConnection/statechange">apis/webrtc/RTCPeerConnection/statechange</a></td>
	<td></td>
	<td data-sort-value="2456913.2643056" class="Modification-date">12 September 2014 18:20:36</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/updateIce" title="apis/webrtc/RTCPeerConnection/updateIce">apis/webrtc/RTCPeerConnection/updateIce</a></td>
	<td class="Summary">Updates the ICE agent process that gathers local candidates and remote candidates.</td>
	<td data-sort-value="2456913.2637963" class="Modification-date">12 September 2014 18:19:52</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCSessionDescription/sdp" title="apis/webrtc/RTCSessionDescription/sdp">apis/webrtc/RTCSessionDescription/sdp</a></td>
	<td class="Summary">The string representation of the SDP object.</td>
	<td data-sort-value="2456913.263125" class="Modification-date">12 September 2014 18:18:54</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCSessionDescription/type" title="apis/webrtc/RTCSessionDescription/type">apis/webrtc/RTCSessionDescription/type</a></td>
	<td class="Summary">The type of SDP object this RTCSessionDescription represents.</td>
	<td data-sort-value="2456913.2628588" class="Modification-date">12 September 2014 18:18:31</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/websocket/CloseEvent/code" title="apis/websocket/CloseEvent/code">apis/websocket/CloseEvent/code</a></td>
	<td class="Summary">The WebSocket connection close code provided by the server.</td>
	<td data-sort-value="2456913.2555208" class="Modification-date">12 September 2014 18:07:57</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/websocket/CloseEvent/reason" title="apis/websocket/CloseEvent/reason">apis/websocket/CloseEvent/reason</a></td>
	<td class="Summary">Indicates the reason the server closed the WebSocket connection.</td>
	<td data-sort-value="2456913.255162" class="Modification-date">12 September 2014 18:07:26</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/websocket/MessageEvent/data" title="apis/websocket/MessageEvent/data">apis/websocket/MessageEvent/data</a></td>
	<td class="Summary">The data from the server.</td>
	<td data-sort-value="2456913.253588" class="Modification-date">12 September 2014 18:05:10</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/websocket/WebSocket/close" title="apis/websocket/WebSocket/close">apis/websocket/WebSocket/close</a></td>
	<td class="Summary">Closes the WebSocket connection or connection attempt, if any.</td>
	<td data-sort-value="2456913.2233218" class="Modification-date">12 September 2014 17:21:35</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/websocket/WebSocket/extensions" title="apis/websocket/WebSocket/extensions">apis/websocket/WebSocket/extensions</a></td>
	<td class="Summary">The extensions selected by the server.</td>
	<td data-sort-value="2456913.2229167" class="Modification-date">12 September 2014 17:21:00</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/websocket/WebSocket/protocol" title="apis/websocket/WebSocket/protocol">apis/websocket/WebSocket/protocol</a></td>
	<td class="Summary">Indicates the name of the sub-protocol the server selected.</td>
	<td data-sort-value="2456913.2206481" class="Modification-date">12 September 2014 17:17:44</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/workers/Worker/onerror" title="apis/workers/Worker/onerror">apis/workers/Worker/onerror</a></td>
	<td class="Summary">An event listener to be called when an error occurs.</td>
	<td data-sort-value="2456913.2158218" class="Modification-date">12 September 2014 17:10:47</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/workers/Worker/onmessage" title="apis/workers/Worker/onmessage">apis/workers/Worker/onmessage</a></td>
	<td class="Summary">An event listener to be called when a message is received from the worker.</td>
	<td data-sort-value="2456913.2155093" class="Modification-date">12 September 2014 17:10:20</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/workers/Worker/postMessage" title="apis/workers/Worker/postMessage">apis/workers/Worker/postMessage</a></td>
	<td class="Summary">Posts a message to the worker with which the object is associated.</td>
	<td data-sort-value="2456913.2150463" class="Modification-date">12 September 2014 17:09:40</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/workers/Worker/terminate" title="apis/workers/Worker/terminate">apis/workers/Worker/terminate</a></td>
	<td class="Summary">Immediately terminates the worker with which the object is associated.</td>
	<td data-sort-value="2456913.2146065" class="Modification-date">12 September 2014 17:09:02</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/workers/WorkerGlobalScope/close" title="apis/workers/WorkerGlobalScope/close">apis/workers/WorkerGlobalScope/close</a></td>
	<td class="Summary">Discards any pending tasks and immediately closes the worker.</td>
	<td data-sort-value="2456913.2136343" class="Modification-date">12 September 2014 17:07:38</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/workers/WorkerGlobalScope/importScripts" title="apis/workers/WorkerGlobalScope/importScripts">apis/workers/WorkerGlobalScope/importScripts</a></td>
	<td class="Summary">Fetches one or more script resources, identified by absolute URLs.</td>
	<td data-sort-value="2456913.2131597" class="Modification-date">12 September 2014 17:06:57</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/workers/WorkerGlobalScope/location" title="apis/workers/WorkerGlobalScope/location">apis/workers/WorkerGlobalScope/location</a></td>
	<td class="Summary">Returns the WorkerLocation object created for the WorkerGlobalScope object when the worker was created.</td>
	<td data-sort-value="2456913.2126157" class="Modification-date">12 September 2014 17:06:10</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/workers/WorkerGlobalScope/navigator" title="apis/workers/WorkerGlobalScope/navigator">apis/workers/WorkerGlobalScope/navigator</a></td>
	<td class="Summary">Returns an instance of the WorkerNavigator interface, which represents the identity and state of the user agent (the client).</td>
	<td data-sort-value="2456913.2120023" class="Modification-date">12 September 2014 17:05:17</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/workers/WorkerGlobalScope/onerror" title="apis/workers/WorkerGlobalScope/onerror">apis/workers/WorkerGlobalScope/onerror</a></td>
	<td class="Summary">An event listener to be called when an error occurs.</td>
	<td data-sort-value="2456913.2115625" class="Modification-date">12 September 2014 17:04:39</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/workers/WorkerGlobalScope/onoffline" title="apis/workers/WorkerGlobalScope/onoffline">apis/workers/WorkerGlobalScope/onoffline</a></td>
	<td class="Summary">An event listener to be called when the worker goes offline.</td>
	<td data-sort-value="2456913.2112384" class="Modification-date">12 September 2014 17:04:11</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/workers/WorkerGlobalScope/ononline" title="apis/workers/WorkerGlobalScope/ononline">apis/workers/WorkerGlobalScope/ononline</a></td>
	<td class="Summary">An event listener to be called when the worker goes online.</td>
	<td data-sort-value="2456913.210706" class="Modification-date">12 September 2014 17:03:25</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/workers/WorkerGlobalScope/self" title="apis/workers/WorkerGlobalScope/self">apis/workers/WorkerGlobalScope/self</a></td>
	<td class="Summary">Returns the WorkerGlobalScope object.</td>
	<td data-sort-value="2456913.2101736" class="Modification-date">12 September 2014 17:02:39</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/workers/WorkerLocation/href" title="apis/workers/WorkerLocation/href">apis/workers/WorkerLocation/href</a></td>
	<td class="Summary">Returns the absolute URL that the object represents.</td>
	<td data-sort-value="2456913.2080208" class="Modification-date">12 September 2014 16:59:33</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/xhr/XMLHttpRequest/abort-event" title="apis/xhr/XMLHttpRequest/abort-event">apis/xhr/XMLHttpRequest/abort-event</a></td>
	<td class="Summary">When the request has been aborted. For instance, by invoking the abort() method.</td>
	<td data-sort-value="2456912.2811806" class="Modification-date">11 September 2014 18:44:54</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/xhr/XMLHttpRequest/error" title="apis/xhr/XMLHttpRequest/error">apis/xhr/XMLHttpRequest/error</a></td>
	<td class="Summary">When the request has failed.</td>
	<td data-sort-value="2456912.2800926" class="Modification-date">11 September 2014 18:43:20</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/xhr/XMLHttpRequest/getResponseHeader" title="apis/xhr/XMLHttpRequest/getResponseHeader">apis/xhr/XMLHttpRequest/getResponseHeader</a></td>
	<td class="Summary">Returns the string containing the text of the specified header, or null if the response has not been received or the header does not exist.</td>
	<td data-sort-value="2456912.2782292" class="Modification-date">11 September 2014 18:40:39</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/xhr/XMLHttpRequest/load" title="apis/xhr/XMLHttpRequest/load">apis/xhr/XMLHttpRequest/load</a></td>
	<td class="Summary">When the request has successfully completed.</td>
	<td data-sort-value="2456912.2776042" class="Modification-date">11 September 2014 18:39:45</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/xhr/XMLHttpRequest/loadend" title="apis/xhr/XMLHttpRequest/loadend">apis/xhr/XMLHttpRequest/loadend</a></td>
	<td class="Summary">When the request has completed (either in success or failure).</td>
	<td data-sort-value="2456912.2771412" class="Modification-date">11 September 2014 18:39:05</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/xhr/XMLHttpRequest/loadstart" title="apis/xhr/XMLHttpRequest/loadstart">apis/xhr/XMLHttpRequest/loadstart</a></td>
	<td class="Summary">When the request starts.</td>
	<td data-sort-value="2456912.2746875" class="Modification-date">11 September 2014 18:35:33</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/xhr/XMLHttpRequest/progress" title="apis/xhr/XMLHttpRequest/progress">apis/xhr/XMLHttpRequest/progress</a></td>
	<td class="Summary">While sending and loading data.</td>
	<td data-sort-value="2456912.2726736" class="Modification-date">11 September 2014 18:32:39</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/xhr/XMLHttpRequest/setRequestHeader" title="apis/xhr/XMLHttpRequest/setRequestHeader">apis/xhr/XMLHttpRequest/setRequestHeader</a></td>
	<td class="Summary">Sets the value of an XMLHttpRequest header.</td>
	<td data-sort-value="2456912.2672685" class="Modification-date">11 September 2014 18:24:52</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/xhr/XMLHttpRequest/status" title="apis/xhr/XMLHttpRequest/status">apis/xhr/XMLHttpRequest/status</a></td>
	<td class="Summary">Returns the HTTP result code (status) of the response to the request.</td>
	<td data-sort-value="2456912.2668287" class="Modification-date">11 September 2014 18:24:14</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/xhr/XMLHttpRequest/timeout-event" title="apis/xhr/XMLHttpRequest/timeout-event">apis/xhr/XMLHttpRequest/timeout-event</a></td>
	<td class="Summary">When the author specified timeout has passed before the request could complete.</td>
	<td data-sort-value="2456912.2639931" class="Modification-date">11 September 2014 18:20:09</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/appcache/ApplicationCache/abort" title="apis/appcache/ApplicationCache/abort">apis/appcache/ApplicationCache/abort</a></td>
	<td class="Summary">Cancels the application cache download process. This method is intended to be used by Web applications showing their own caching progress UI, in case the user wants to stop the update (e.g., because bandwidth is limited).</td>
	<td data-sort-value="2456875.2084606" class="Modification-date">5 August 2014 17:00:11</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/timing/methods/msWriteProfilerMark" title="apis/timing/methods/msWriteProfilerMark">apis/timing/methods/msWriteProfilerMark</a></td>
	<td></td>
	<td data-sort-value="2456846.2483333" class="Modification-date">7 July 2014 17:57:36</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/timing/methods/sample" title="apis/timing/methods/sample">apis/timing/methods/sample</a></td>
	<td></td>
	<td data-sort-value="2456846.2462384" class="Modification-date">7 July 2014 17:54:35</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/timing/objects/FrameRequestCallback" title="apis/timing/objects/FrameRequestCallback">apis/timing/objects/FrameRequestCallback</a></td>
	<td></td>
	<td data-sort-value="2456846.2434722" class="Modification-date">7 July 2014 17:50:36</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/timing/properties/performance" title="apis/timing/properties/performance">apis/timing/properties/performance</a></td>
	<td></td>
	<td data-sort-value="2456846.2334954" class="Modification-date">7 July 2014 17:36:14</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/LocalMediaStream/stop" title="apis/webrtc/LocalMediaStream/stop">apis/webrtc/LocalMediaStream/stop</a></td>
	<td class="Summary">Permanently halts the generation of data for the tracks' sources and removes the references to the sources.</td>
	<td data-sort-value="2456840.4967708" class="Modification-date">1 July 2014 23:55:21</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStream/audioTracks" title="apis/webrtc/MediaStream/audioTracks">apis/webrtc/MediaStream/audioTracks</a></td>
	<td class="Summary">The MediaStreamTrackList object representing the audio tracks.</td>
	<td data-sort-value="2456840.3609491" class="Modification-date">1 July 2014 20:39:46</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStream/ended" title="apis/webrtc/MediaStream/ended">apis/webrtc/MediaStream/ended</a></td>
	<td class="Summary">True if the ended event has fired on the MediaStream object.</td>
	<td data-sort-value="2456840.360625" class="Modification-date">1 July 2014 20:39:18</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStream/label" title="apis/webrtc/MediaStream/label">apis/webrtc/MediaStream/label</a></td>
	<td class="Summary">A globally unique identifier (GUID) of 36 characters that describes the media stream.</td>
	<td data-sort-value="2456840.3601042" class="Modification-date">1 July 2014 20:38:33</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStream/onended" title="apis/webrtc/MediaStream/onended">apis/webrtc/MediaStream/onended</a></td>
	<td class="Summary">Handles the ended event when fired on the MediaStream object.</td>
	<td data-sort-value="2456840.3595718" class="Modification-date">1 July 2014 20:37:47</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStream/videoTracks" title="apis/webrtc/MediaStream/videoTracks">apis/webrtc/MediaStream/videoTracks</a></td>
	<td class="Summary">The MediaStreamTrackList object representing the video tracks.</td>
	<td data-sort-value="2456840.356412" class="Modification-date">1 July 2014 20:33:14</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrack" title="apis/webrtc/MediaStreamTrack">apis/webrtc/MediaStreamTrack</a></td>
	<td class="Summary">A MediaStreamTrack is one of two kinds, audio or video, and represents the media source, such as a camera.</td>
	<td data-sort-value="2456840.3303009" class="Modification-date">1 July 2014 19:55:38</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrack/enabled" title="apis/webrtc/MediaStreamTrack/enabled">apis/webrtc/MediaStreamTrack/enabled</a></td>
	<td class="Summary">True if the track is still associated with its source.</td>
	<td data-sort-value="2456840.3297454" class="Modification-date">1 July 2014 19:54:50</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrack/ended" title="apis/webrtc/MediaStreamTrack/ended">apis/webrtc/MediaStreamTrack/ended</a></td>
	<td class="Summary">The MediaStreamTrack object's source will not provide data; this may be caused by the following:
<ul><li> the user has revoked permissions on the application</li>
<li> the source device has been disconnected</li>
<li> the remote peer has stopped sending data</li>
<li> the stop() method was invoked</li></ul></td>
	<td data-sort-value="2456840.3292245" class="Modification-date">1 July 2014 19:54:05</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrack/kind" title="apis/webrtc/MediaStreamTrack/kind">apis/webrtc/MediaStreamTrack/kind</a></td>
	<td class="Summary">The value, either <b>audio</b> or <b>video</b> for the source of the track.</td>
	<td data-sort-value="2456840.3282639" class="Modification-date">1 July 2014 19:52:42</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrack/label" title="apis/webrtc/MediaStreamTrack/label">apis/webrtc/MediaStreamTrack/label</a></td>
	<td class="Summary">A user agent-assigned string that identifies the track source, as in "internal microphone."</td>
	<td data-sort-value="2456840.3272222" class="Modification-date">1 July 2014 19:51:12</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrack/muted" title="apis/webrtc/MediaStreamTrack/muted">apis/webrtc/MediaStreamTrack/muted</a></td>
	<td class="Summary">The MediaStreamTrack object's source is temporarily unable to provide data.</td>
	<td data-sort-value="2456840.3261458" class="Modification-date">1 July 2014 19:49:39</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrack/onended" title="apis/webrtc/MediaStreamTrack/onended">apis/webrtc/MediaStreamTrack/onended</a></td>
	<td class="Summary">Handles the ended event when fired on the MediaStream object.</td>
	<td data-sort-value="2456840.3247222" class="Modification-date">1 July 2014 19:47:36</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrack/onmute" title="apis/webrtc/MediaStreamTrack/onmute">apis/webrtc/MediaStreamTrack/onmute</a></td>
	<td class="Summary">Handles the muted event when fired on the MediaStream object.</td>
	<td data-sort-value="2456840.3173148" class="Modification-date">1 July 2014 19:36:56</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrack/readyState" title="apis/webrtc/MediaStreamTrack/readyState">apis/webrtc/MediaStreamTrack/readyState</a></td>
	<td class="Summary">The track's ready state; values.</td>
	<td data-sort-value="2456840.3166435" class="Modification-date">1 July 2014 19:35:58</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrack/unmuted" title="apis/webrtc/MediaStreamTrack/unmuted">apis/webrtc/MediaStreamTrack/unmuted</a></td>
	<td class="Summary">The MediaStreamTrack object's source has resumed providing data.</td>
	<td data-sort-value="2456840.315787" class="Modification-date">1 July 2014 19:34:44</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrackList" title="apis/webrtc/MediaStreamTrackList">apis/webrtc/MediaStreamTrackList</a></td>
	<td class="Summary">A MediaStream has two MediaStreamTrackList objects, one for the video tracks and one for the audio tracks.</td>
	<td data-sort-value="2456840.3134491" class="Modification-date">1 July 2014 19:31:22</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrackList/add" title="apis/webrtc/MediaStreamTrackList/add">apis/webrtc/MediaStreamTrackList/add</a></td>
	<td class="Summary">Adds a MediaStreamTrack to this track list.</td>
	<td data-sort-value="2456840.3123958" class="Modification-date">1 July 2014 19:29:51</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrackList/addtrack" title="apis/webrtc/MediaStreamTrackList/addtrack">apis/webrtc/MediaStreamTrackList/addtrack</a></td>
	<td class="Summary">A MediaStreamTrack has been added to the list.</td>
	<td data-sort-value="2456840.3117245" class="Modification-date">1 July 2014 19:28:53</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrackList/item" title="apis/webrtc/MediaStreamTrackList/item">apis/webrtc/MediaStreamTrackList/item</a></td>
	<td class="Summary">Returns the MediaStreamTrack at the specified index value.</td>
	<td data-sort-value="2456840.3112963" class="Modification-date">1 July 2014 19:28:16</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrackList/length" title="apis/webrtc/MediaStreamTrackList/length">apis/webrtc/MediaStreamTrackList/length</a></td>
	<td class="Summary">The number of tracks in the list.</td>
	<td data-sort-value="2456840.3109722" class="Modification-date">1 July 2014 19:27:48</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrackList/onaddtrack" title="apis/webrtc/MediaStreamTrackList/onaddtrack">apis/webrtc/MediaStreamTrackList/onaddtrack</a></td>
	<td class="Summary">Handles the addtrack event.</td>
	<td data-sort-value="2456840.3106019" class="Modification-date">1 July 2014 19:27:16</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrackList/onremovetrack" title="apis/webrtc/MediaStreamTrackList/onremovetrack">apis/webrtc/MediaStreamTrackList/onremovetrack</a></td>
	<td class="Summary">Handles the removetrack event.</td>
	<td data-sort-value="2456840.3102546" class="Modification-date">1 July 2014 19:26:46</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrackList/remove" title="apis/webrtc/MediaStreamTrackList/remove">apis/webrtc/MediaStreamTrackList/remove</a></td>
	<td class="Summary">Removes a MediaStreamTrack from this track list.</td>
	<td data-sort-value="2456840.3098843" class="Modification-date">1 July 2014 19:26:14</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/MediaStreamTrackList/removetrack" title="apis/webrtc/MediaStreamTrackList/removetrack">apis/webrtc/MediaStreamTrackList/removetrack</a></td>
	<td class="Summary">A MediaStreamTrack has been removed from the list.</td>
	<td data-sort-value="2456840.309213" class="Modification-date">1 July 2014 19:25:16</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCDataChannel/binaryType" title="apis/webrtc/RTCDataChannel/binaryType">apis/webrtc/RTCDataChannel/binaryType</a></td>
	<td class="Summary">Returns the value to which it was last set; on creation, must be initialized to the string "blob".</td>
	<td data-sort-value="2456840.2775231" class="Modification-date">1 July 2014 18:39:38</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCDataChannel/bufferedAmount" title="apis/webrtc/RTCDataChannel/bufferedAmount">apis/webrtc/RTCDataChannel/bufferedAmount</a></td>
	<td class="Summary">Returns the number of bytes of application data that have been queued using send() but that (as of the last time the event loop started executing a task) have not yet been transmitted to the network.</td>
	<td data-sort-value="2456840.2769676" class="Modification-date">1 July 2014 18:38:50</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCDataChannel/close" title="apis/webrtc/RTCDataChannel/close">apis/webrtc/RTCDataChannel/close</a></td>
	<td class="Summary">Closes the RTCDataChannel.</td>
	<td data-sort-value="2456840.2737616" class="Modification-date">1 July 2014 18:34:13</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCDataChannel/label" title="apis/webrtc/RTCDataChannel/label">apis/webrtc/RTCDataChannel/label</a></td>
	<td class="Summary">A unique identifier that can be used to distinguish this RTCDataChannel object from other RTCDataChannel objects.</td>
	<td data-sort-value="2456840.2732523" class="Modification-date">1 July 2014 18:33:29</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCDataChannel/onclose" title="apis/webrtc/RTCDataChannel/onclose">apis/webrtc/RTCDataChannel/onclose</a></td>
	<td class="Summary">An event listener to be called when an RTCDataChannel is closed.</td>
	<td data-sort-value="2456840.2727546" class="Modification-date">1 July 2014 18:32:46</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCDataChannel/onerror" title="apis/webrtc/RTCDataChannel/onerror">apis/webrtc/RTCDataChannel/onerror</a></td>
	<td class="Summary">An event listener to be called when an error occurs.</td>
	<td data-sort-value="2456840.2721875" class="Modification-date">1 July 2014 18:31:57</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCDataChannel/onmessage" title="apis/webrtc/RTCDataChannel/onmessage">apis/webrtc/RTCDataChannel/onmessage</a></td>
	<td class="Summary">An event listener to be called when a message is received.</td>
	<td data-sort-value="2456840.2718287" class="Modification-date">1 July 2014 18:31:26</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCDataChannel/onopen" title="apis/webrtc/RTCDataChannel/onopen">apis/webrtc/RTCDataChannel/onopen</a></td>
	<td class="Summary">An event listener to be called when an RTCDataChannel is opened.</td>
	<td data-sort-value="2456840.2703009" class="Modification-date">1 July 2014 18:29:14</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCDataChannel/readyState" title="apis/webrtc/RTCDataChannel/readyState">apis/webrtc/RTCDataChannel/readyState</a></td>
	<td class="Summary">Represents the state of the RTCDataChannel object.</td>
	<td data-sort-value="2456840.2694329" class="Modification-date">1 July 2014 18:27:59</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCDataChannel/reliable" title="apis/webrtc/RTCDataChannel/reliable">apis/webrtc/RTCDataChannel/reliable</a></td>
	<td class="Summary">Returns true if the RTCDataChannel is reliable, and false otherwise.</td>
	<td data-sort-value="2456840.2676505" class="Modification-date">1 July 2014 18:25:25</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCDataChannel/send" title="apis/webrtc/RTCDataChannel/send">apis/webrtc/RTCDataChannel/send</a></td>
	<td class="Summary">Sends a message (<i>data</i>) on the RTCDataChannel’s underlying data transport.</td>
	<td data-sort-value="2456840.2663194" class="Modification-date">1 July 2014 18:23:30</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCIceCandidate" title="apis/webrtc/RTCIceCandidate">apis/webrtc/RTCIceCandidate</a></td>
	<td></td>
	<td data-sort-value="2456840.2640394" class="Modification-date">1 July 2014 18:20:13</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection" title="apis/webrtc/RTCPeerConnection">apis/webrtc/RTCPeerConnection</a></td>
	<td class="Summary">Provides for the connection between remote peers, the transmission of locally generated MediaStream data and arbitrary data between peers.</td>
	<td data-sort-value="2456840.2627894" class="Modification-date">1 July 2014 18:18:25</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/addIceCandidate" title="apis/webrtc/RTCPeerConnection/addIceCandidate">apis/webrtc/RTCPeerConnection/addIceCandidate</a></td>
	<td class="Summary">Provides a remote candidate to the ICE agent.</td>
	<td data-sort-value="2456840.2616667" class="Modification-date">1 July 2014 18:16:48</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/close" title="apis/webrtc/RTCPeerConnection/close">apis/webrtc/RTCPeerConnection/close</a></td>
	<td class="Summary">Closes a peer connection, stops all active ICE processing and any active streaming, and releases any relevant resources such as TURN permissions.</td>
	<td data-sort-value="2456839.4635764" class="Modification-date">30 June 2014 23:07:33</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/createAnswer" title="apis/webrtc/RTCPeerConnection/createAnswer">apis/webrtc/RTCPeerConnection/createAnswer</a></td>
	<td class="Summary">Creates a session description compatible with the remote configuration.</td>
	<td data-sort-value="2456839.4629051" class="Modification-date">30 June 2014 23:06:35</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/createOffer" title="apis/webrtc/RTCPeerConnection/createOffer">apis/webrtc/RTCPeerConnection/createOffer</a></td>
	<td class="Summary">Creates a session description compatible with the local configuration.</td>
	<td data-sort-value="2456839.4600347" class="Modification-date">30 June 2014 23:02:27</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/getIdentityAssertion" title="apis/webrtc/RTCPeerConnection/getIdentityAssertion">apis/webrtc/RTCPeerConnection/getIdentityAssertion</a></td>
	<td class="Summary">Provides an identity assertion.</td>
	<td data-sort-value="2456839.4589468" class="Modification-date">30 June 2014 23:00:53</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/getStats" title="apis/webrtc/RTCPeerConnection/getStats">apis/webrtc/RTCPeerConnection/getStats</a></td>
	<td class="Summary">Retrieves status information for a given <a href="/wiki/apis/webrtc/MediaStreamTrack" title="apis/webrtc/MediaStreamTrack">MediaStreamTrack</a>.</td>
	<td data-sort-value="2456839.4584491" class="Modification-date">30 June 2014 23:00:10</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/iceGatheringState" title="apis/webrtc/RTCPeerConnection/iceGatheringState">apis/webrtc/RTCPeerConnection/iceGatheringState</a></td>
	<td class="Summary">Returns the gathering state of the ICE agent.</td>
	<td data-sort-value="2456839.4563773" class="Modification-date">30 June 2014 22:57:11</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/iceState" title="apis/webrtc/RTCPeerConnection/iceState">apis/webrtc/RTCPeerConnection/iceState</a></td>
	<td class="Summary">Returns the ICE state of the ICE agent.</td>
	<td data-sort-value="2456839.4552083" class="Modification-date">30 June 2014 22:55:30</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/icecandidate" title="apis/webrtc/RTCPeerConnection/icecandidate">apis/webrtc/RTCPeerConnection/icecandidate</a></td>
	<td></td>
	<td data-sort-value="2456839.4526157" class="Modification-date">30 June 2014 22:51:46</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/icechange" title="apis/webrtc/RTCPeerConnection/icechange">apis/webrtc/RTCPeerConnection/icechange</a></td>
	<td></td>
	<td data-sort-value="2456839.4521065" class="Modification-date">30 June 2014 22:51:02</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/quota_management/requestQuota" title="apis/quota management/requestQuota">apis/quota management/requestQuota</a></td>
	<td class="Summary">Requests a new quota for the requesting application.</td>
	<td data-sort-value="2456834.5251389" class="Modification-date">26 June 2014 00:36:12</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/quota_management/queryUsageAndQuota" title="apis/quota management/queryUsageAndQuota">apis/quota management/queryUsageAndQuota</a></td>
	<td class="Summary">Queries the current usage (how much data is stored) and quota available for the requesting application.</td>
	<td data-sort-value="2456834.5248958" class="Modification-date">26 June 2014 00:35:51</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/quota_management/StorageQuota" title="apis/quota management/StorageQuota">apis/quota management/StorageQuota</a></td>
	<td class="Summary">Provides a means to query and request storage usage and quota information.</td>
	<td data-sort-value="2456834.523588" class="Modification-date">26 June 2014 00:33:58</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/network_information/NetworkInformation/connection" title="apis/network information/NetworkInformation/connection">apis/network information/NetworkInformation/connection</a></td>
	<td class="Summary">The object from which connection information is accessed.</td>
	<td data-sort-value="2456834.4849884" class="Modification-date">25 June 2014 23:38:23</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/network_information/Connection/onchange" title="apis/network information/Connection/onchange">apis/network information/Connection/onchange</a></td>
	<td class="Summary">Handles the change event, fired when the Connection changes.</td>
	<td data-sort-value="2456834.4842245" class="Modification-date">25 June 2014 23:37:17</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/network_information/Connection/metered" title="apis/network information/Connection/metered">apis/network information/Connection/metered</a></td>
	<td class="Summary">A connection is metered when the user's connection is subject to a limitation from his Internet Service Provider strong enough to request web applications to be careful with the bandwidth usage.</td>
	<td data-sort-value="2456834.4837384" class="Modification-date">25 June 2014 23:36:35</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/network_information/Connection/change" title="apis/network information/Connection/change">apis/network information/Connection/change</a></td>
	<td class="Summary">Fires when the Connection changes.</td>
	<td data-sort-value="2456834.483287" class="Modification-date">25 June 2014 23:35:56</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/network_information/Connection/bandwidth" title="apis/network information/Connection/bandwidth">apis/network information/Connection/bandwidth</a></td>
	<td class="Summary">An estimation of the current bandwidth in MB/s (Megabytes per seconds) available.</td>
	<td data-sort-value="2456834.4828704" class="Modification-date">25 June 2014 23:35:20</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/network_information/Connection" title="apis/network information/Connection">apis/network information/Connection</a></td>
	<td class="Summary">Provides a handle to the device's connection information.</td>
	<td data-sort-value="2456834.4820255" class="Modification-date">25 June 2014 23:34:07</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/MediaStream/ended" title="apis/MediaStream/ended">apis/MediaStream/ended</a></td>
	<td class="Summary">All tracks of the MediaStream object have ended; the MediaStream is said to be finished.</td>
	<td data-sort-value="2456829.5215972" class="Modification-date">21 June 2014 00:31:06</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/identityresult" title="apis/webrtc/RTCPeerConnection/identityresult">apis/webrtc/RTCPeerConnection/identityresult</a></td>
	<td></td>
	<td data-sort-value="2456826.0491319" class="Modification-date">17 June 2014 13:10:45</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/css/media_queries/apis/properties/type" title="css/media queries/apis/properties/type">css/media queries/apis/properties/type</a></td>
	<td class="Summary">Gets the media type of the object that displays the <a href="/wiki/dom/Document" title="dom/Document">Document</a> object</td>
	<td data-sort-value="2456826.002037" class="Modification-date">17 June 2014 12:02:56</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/css/media_queries/apis/removeListener" title="css/media queries/apis/removeListener">css/media queries/apis/removeListener</a></td>
	<td></td>
	<td data-sort-value="2456825.9912037" class="Modification-date">17 June 2014 11:47:20</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/css/media_queries/apis/media" title="css/media queries/apis/media">css/media queries/apis/media</a></td>
	<td></td>
	<td data-sort-value="2456825.9907986" class="Modification-date">17 June 2014 11:46:45</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/css/media_queries/apis/matches" title="css/media queries/apis/matches">css/media queries/apis/matches</a></td>
	<td></td>
	<td data-sort-value="2456825.9903241" class="Modification-date">17 June 2014 11:46:04</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/css/media_queries/apis/matchMedium" title="css/media queries/apis/matchMedium">css/media queries/apis/matchMedium</a></td>
	<td class="Summary">Indicates whether the document currently matches a media query.</td>
	<td data-sort-value="2456825.9895949" class="Modification-date">17 June 2014 11:45:01</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/css/media_queries/apis/matchMedia" title="css/media queries/apis/matchMedia">css/media queries/apis/matchMedia</a></td>
	<td></td>
	<td data-sort-value="2456825.9887384" class="Modification-date">17 June 2014 11:43:47</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/css/media_queries/apis/handleChange" title="css/media queries/apis/handleChange">css/media queries/apis/handleChange</a></td>
	<td></td>
	<td data-sort-value="2456825.9879167" class="Modification-date">17 June 2014 11:42:36</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/css/media_queries/apis/addListener" title="css/media queries/apis/addListener">css/media queries/apis/addListener</a></td>
	<td></td>
	<td data-sort-value="2456825.9875" class="Modification-date">17 June 2014 11:42:00</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/css/media_queries/apis/StyleMedia" title="css/media queries/apis/StyleMedia">css/media queries/apis/StyleMedia</a></td>
	<td class="Summary">A CSS media related functionality and information.</td>
	<td data-sort-value="2456825.9855671" class="Modification-date">17 June 2014 11:39:13</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/css/media_queries/apis/MediaQueryListListener" title="css/media queries/apis/MediaQueryListListener">css/media queries/apis/MediaQueryListListener</a></td>
	<td></td>
	<td data-sort-value="2456825.9846759" class="Modification-date">17 June 2014 11:37:56</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/css/media_queries/apis/MediaQueryList" title="css/media queries/apis/MediaQueryList">css/media queries/apis/MediaQueryList</a></td>
	<td></td>
	<td data-sort-value="2456825.9838657" class="Modification-date">17 June 2014 11:36:46</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/css/high_contrast_modeapis/properties/ms-high-contrast-adjust" title="css/high contrast modeapis/properties/ms-high-contrast-adjust">css/high contrast modeapis/properties/ms-high-contrast-adjust</a></td>
	<td></td>
	<td data-sort-value="2456825.9786343" class="Modification-date">17 June 2014 11:29:14</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/appcache/ApplicationCache/oncached" title="apis/appcache/ApplicationCache/oncached">apis/appcache/ApplicationCache/oncached</a></td>
	<td class="Summary">The resources listed in the manifest have been downloaded, and the application is now cached.</td>
	<td data-sort-value="2456466.2674074" class="Modification-date">22 June 2013 18:25:04</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/appcache/ApplicationCache/onerror" title="apis/appcache/ApplicationCache/onerror">apis/appcache/ApplicationCache/onerror</a></td>
	<td class="Summary">Indicates an error has occurred.</td>
	<td data-sort-value="2456365.3254282" class="Modification-date">13 March 2013 19:48:37</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/appcache/ApplicationCache/ondownloading" title="apis/appcache/ApplicationCache/ondownloading">apis/appcache/ApplicationCache/ondownloading</a></td>
	<td class="Summary">The user agent has found an update and is fetching it, or is downloading the resources listed by the manifest for the first time.</td>
	<td data-sort-value="2456365.3251157" class="Modification-date">13 March 2013 19:48:10</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/appcache/ApplicationCache/onchecking" title="apis/appcache/ApplicationCache/onchecking">apis/appcache/ApplicationCache/onchecking</a></td>
	<td class="Summary">The user agent is checking for an update, or attempting to download the manifest for the first time. This is always the first event in the sequence.</td>
	<td data-sort-value="2456365.3247454" class="Modification-date">13 March 2013 19:47:38</td>
</tr></tbody><tfoot></tfoot></table>