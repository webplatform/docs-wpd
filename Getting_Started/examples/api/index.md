---
title: WPD:Getting Started/examples/api
---
<h1><span class="mw-headline" id="API_pages_needing_examples">API pages needing examples</span></h1>
<p>Total: 428
</p>
<table class="sortable wikitable smwtable" width="100%">
<tr><th class="Path">Path</th>
<th class="Summary">Summary</th>
<th class="Modification-date">Modification date</th></tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webrtc/RTCPeerConnection/onremovestream" title="apis/webrtc/RTCPeerConnection/onremovestream">apis/webrtc/RTCPeerConnection/onremovestream</a></td>
	<td class="Summary">Handles the <a href="/wiki/apis/webrtc/RTCPeerConnection/removeStream" title="apis/webrtc/RTCPeerConnection/removeStream">removeStream</a> event for when <a href="/wiki/apis/webrtc/RTCPeerConnection/setRemoteDescription" title="apis/webrtc/RTCPeerConnection/setRemoteDescription">setRemoteDescription()</a> is called to remove a <a href="/wiki/apis/webrtc/MediaStream" title="apis/webrtc/MediaStream">MediaStream</a> object on the remote peer.</td>
	<td data-sort-value="2457226.5662963" class="Modification-date">23 July 2015 01:35:28</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/audio-video/video" title="apis/audio-video/video">apis/audio-video/video</a></td>
	<td class="Summary">HTML Video element allows creator of a HTML document or view of a Web Application to embed a video for display when a user visits the view or opens HTML document in a web browser.</td>
	<td data-sort-value="2457140.3586343" class="Modification-date">27 April 2015 20:36:26</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/ScriptProcessorNode/onaudioprocess" title="apis/webaudio/ScriptProcessorNode/onaudioprocess">apis/webaudio/ScriptProcessorNode/onaudioprocess</a></td>
	<td class="Summary">An event listener which is called periodically for audio processing. An event of type <a href="/wiki/apis/webaudio/AudioProcessingEvent" title="apis/webaudio/AudioProcessingEvent"><b>AudioProcessingEvent</b></a> will be passed to the event handler.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.326331" class="Modification-date">31 December 2014 19:49:55</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webaudio/ScriptProcessorNode/bufferSize" title="apis/webaudio/ScriptProcessorNode/bufferSize">apis/webaudio/ScriptProcessorNode/bufferSize</a></td>
	<td class="Summary">The size of the buffer (in sample-frames) which needs to be processed each time <a href="/wiki/apis/webaudio/ScriptProcessorNode/onaudioprocess" title="apis/webaudio/ScriptProcessorNode/onaudioprocess"><b>onaudioprocess</b></a> is called. Legal values are 256, 512, 1024, 2048, 4096, 8192, and 16384.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.3257986" class="Modification-date">31 December 2014 19:49:09</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/OscillatorNode/setWaveTable" title="apis/webaudio/OscillatorNode/setWaveTable">apis/webaudio/OscillatorNode/setWaveTable</a></td>
	<td class="Summary">Sets an arbitrary custom periodic waveform given a <a href="/wiki/apis/webaudio/WaveTable" title="apis/webaudio/WaveTable"><b>WaveTable</b></a>.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.3040856" class="Modification-date">31 December 2014 19:17:53</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webaudio/OscillatorNode/playbackState" title="apis/webaudio/OscillatorNode/playbackState">apis/webaudio/OscillatorNode/playbackState</a></td>
	<td class="Summary">The playback state, initialized to UNSCHEDULED_STATE, progressing through SCHEDULED_STATE, PLAYING_STATE, and FINISHED_STATE.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.3035301" class="Modification-date">31 December 2014 19:17:05</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioProcessingEvent/playbackTime" title="apis/webaudio/AudioProcessingEvent/playbackTime">apis/webaudio/AudioProcessingEvent/playbackTime</a></td>
	<td class="Summary">The time when the audio will be played, in the same time coordinate system as <a href="/wiki/apis/webaudio/AudioContext/currentTime" title="apis/webaudio/AudioContext/currentTime"><b>AudioContext.currentTime</b></a>. <a href="/wiki/apis/webaudio/AudioProcessingEvent/playbackTime" title="apis/webaudio/AudioProcessingEvent/playbackTime"><b>playbackTime</b></a> allows for very tight synchronization between processing directly in JavaScript with the other events in the context's rendering graph.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2729977" class="Modification-date">31 December 2014 18:33:07</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioProcessingEvent/outputBuffer" title="apis/webaudio/AudioProcessingEvent/outputBuffer">apis/webaudio/AudioProcessingEvent/outputBuffer</a></td>
	<td class="Summary">An <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a> where the output audio data should be written. It will have a number of channels equal to the <b>numberOfOutputChannels</b> parameter of the <a href="/wiki/apis/webaudio/AudioContext/createScriptProcessor" title="apis/webaudio/AudioContext/createScriptProcessor"><b>createScriptProcessor()</b></a> method. Script code within the scope of the <a href="/wiki/apis/webaudio/ScriptProcessorNode/onaudioprocess" title="apis/webaudio/ScriptProcessorNode/onaudioprocess"><b>onaudioprocess</b></a> function is expected to modify the <b>Float32Array</b> arrays representing channel data in this <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a>. Any script modifications to this <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a> outside of this scope will not produce any audible effects.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2724884" class="Modification-date">31 December 2014 18:32:23</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioProcessingEvent/node" title="apis/webaudio/AudioProcessingEvent/node">apis/webaudio/AudioProcessingEvent/node</a></td>
	<td class="Summary">The <a href="/wiki/apis/webaudio/ScriptProcessorNode" title="apis/webaudio/ScriptProcessorNode"><b>ScriptProcessorNode</b></a> associated with this processing event.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2719444" class="Modification-date">31 December 2014 18:31:36</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioProcessingEvent/inputBuffer" title="apis/webaudio/AudioProcessingEvent/inputBuffer">apis/webaudio/AudioProcessingEvent/inputBuffer</a></td>
	<td class="Summary">An <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a> containing the input audio data. It will have a number of channels equal to the <b>numberOfInputChannels</b> parameter of the <a href="/wiki/apis/webaudio/AudioContext/createScriptProcessor" title="apis/webaudio/AudioContext/createScriptProcessor"><b>createScriptProcessor()</b></a> method. This <a href="/wiki/apis/webaudio/AudioBuffer" title="apis/webaudio/AudioBuffer"><b>AudioBuffer</b></a> is only valid while in the scope of the <a href="/wiki/apis/webaudio/ScriptProcessorNode/onaudioprocess" title="apis/webaudio/ScriptProcessorNode/onaudioprocess"><b>onaudioprocess</b></a> function. Its values will be meaningless outside of this scope.
<b>Deprecated; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2706829" class="Modification-date">31 December 2014 18:29:47</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioParam/minValue" title="apis/webaudio/AudioParam/minValue">apis/webaudio/AudioParam/minValue</a></td>
	<td class="Summary">Nominal minimum value. The value attribute may be set lower than this value.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2624884" class="Modification-date">31 December 2014 18:17:59</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioParam/maxValue" title="apis/webaudio/AudioParam/maxValue">apis/webaudio/AudioParam/maxValue</a></td>
	<td class="Summary">Nominal maximum value. The value attribute may be set higher than this value.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2618866" class="Modification-date">31 December 2014 18:17:07</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioParam/computedValue" title="apis/webaudio/AudioParam/computedValue">apis/webaudio/AudioParam/computedValue</a></td>
	<td class="Summary">The final value controlling the audio DSP, calculated at each time, which is either the value set directly to the value attribute or, if there are any scheduled parameter changes (automation events), the value as calculated from these events.
<b>Not in spec; deletion candidate. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457023.2548264" class="Modification-date">31 December 2014 18:06:57</td>
</tr>
<tr class="row-even">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioDestinationNode/numberOfChannels" title="apis/webaudio/AudioDestinationNode/numberOfChannels">apis/webaudio/AudioDestinationNode/numberOfChannels</a></td>
	<td class="Summary">The number of channels of the destination's input. This value will default to 2, and may be set to any non-zero value less than or equal to <a href="/wiki/apis/webaudio/AudioDestinationNode/maxChannelCount" title="apis/webaudio/AudioDestinationNode/maxChannelCount"><b>maxChannelCount</b></a>. An exception will be thrown if this value is not within the valid range.
<b>Not in spec; deletion candidate. Possibly confused with AudioBuffer/numberOfChannels. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457021.3915625" class="Modification-date">29 December 2014 21:23:51</td>
</tr>
<tr class="row-odd">
	<td class="Path"><a href="/wiki/apis/webaudio/AudioContext/createWaveTable" title="apis/webaudio/AudioContext/createWaveTable">apis/webaudio/AudioContext/createWaveTable</a></td>
	<td class="Summary">Creates a <a href="/wiki/apis/webaudio/WaveTable" title="apis/webaudio/WaveTable"><b>WaveTable</b></a> representing a waveform containing arbitrary harmonic content. The real and imag parameters must be of type <b>Float32Array</b> of equal lengths greater than zero and less than or equal to 4096 or an exception will be thrown. These parameters specify the Fourier coefficients of a Fourier series representing the partials of a periodic waveform. The created <a href="/wiki/apis/webaudio/WaveTable" title="apis/webaudio/WaveTable"><b>WaveTable</b></a> will be used with an <a href="/wiki/apis/webaudio/OscillatorNode" title="apis/webaudio/OscillatorNode"><b>OscillatorNode</b></a> and will represent a normalized time-domain waveform having maximum absolute peak value of 1. Another way of saying this is that the generated waveform of an <a href="/wiki/apis/webaudio/OscillatorNode" title="apis/webaudio/OscillatorNode"><b>OscillatorNode</b></a> will have maximum peak value at 0dBFS. Conveniently, this corresponds to the full-range of the signal values used by the Web Audio API. Because the <a href="/wiki/apis/webaudio/WaveTable" title="apis/webaudio/WaveTable"><b>WaveTable</b></a> will be normalized on creation, the real and imag parameters represent relative values.
<b>Out of date; removed from spec. See <a rel="nofollow" class="external free" href="http://webaudio.github.io/web-audio-api/">http://webaudio.github.io/web-audio-api/</a>.</b></td>
	<td data-sort-value="2457016.2891782" class="Modification-date">24 December 2014 18:56:25</td>
</tr>	<tr class="smwfooter"><td class="sortbottom" colspan="3"> <a rel="nofollow" class="external text" href="//docs.webplatform.org/w/index.php?title=Special:Ask&amp;x=-5B-5BPath%3A%3A~%2Aapis-2F%2A-5D-5D-20-5B-5BContent-20quality-20flag%3A%3A~Examples-20Needed-5D-5D%2F-3FPath%2F-3FSummary%2F-3FModification-20date&amp;format=broadtable&amp;limit=15&amp;sort=Modification%20date&amp;order=desc&amp;headers=plain&amp;mainlabel=-&amp;searchlabel=%27%27%27More%20results%27%27%27&amp;default=%7B%7B%7Bdefault_text%7D%7D%7D&amp;offset=15"><b>More results</b></a></td></tr>
</table>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:7646-0!*!0!*!*!*!*!esi=1 and timestamp 20150731183713 and revision id 28617
 -->
