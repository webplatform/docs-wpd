A list of required actions in the long run, mostly due to the fact that the current templates do not support certain scenarios.
*Remove "Non standard" from the summary once there is an automatic indication in the listing pages (non exhaustive, unfortunately) -
**[[dom/methods/cancelBubble]]
**[[dom/methods/ChooseColorDlg]]
**[[dom/properties/canHaveChildren]]
**[[dom/properties/compatible]]
**[[dom/clipboardData]]
**[[dom/methods/getAttribute_(userProfile)]]
**[[dom/methods/dragDrop]]
**[[dom/properties/cpuClass]]
**[[dom/userProfile]]
**[[dom/methods/createPopup]]
**[[dom/properties/srcElement]]
**[[dom/properties/reason2]]
**[[dom/properties/which]]
**[[dom/properties/x (mouseevent)]]
**[[dom/properties/y (mouseevent)]]
**[[dom/properties/boundElements]]
**[[dom/methods/releaseCapture]]
**[[dom/properties/returnValue]]
**[[dom/properties/fromElement]]
**[[dom/methods/setCapture]]
**[[dom/methods/fireEvent]]
**[[dom/methods/applyElement]]
*Miscellaneous -
**[[dom/methods/getAttribute_(userProfile)]], [[dom/properties/cpuClass]], [[dom/userProfile]] - apply to [[dom/Navigator]] when it exists
**[[cssom/ClientRect]] - needs further work?
**[[dom/methods/replaceState]] - explain the buggy behavior of Safari 5 and later.
**[[Template:API_Object_Property_New]] - work in progress.
**[[dom/properties/reason2]] - find the event that uses this property.
**[[dom/methods/cancelBubble]] - should probably be removed.
**[[dom/objects/dataTransfer]] - change its URL to be property related one or something (?).
**[[dom/clipboardData]] - needs an offer for an alternative, standard (track) implementation (event.dataTransfer?)
*Needs support for multiple values in the "Applies to..." field -
{|
! Page
! Future Multiple "Applies to..." Values
|-
|[[dom/methods/attachEvent]]
|[[dom/document]], [[dom/window]], [[dom/Node]]
|-
|[[dom/methods/getModifierState]]
|[[dom/objects/KeyboardEvent]],
[[dom/objects/MouseEvent]], more?
|-
|[[dom/properties/fgColor]]
|[[dom/document]], [[dom/HTMLBodyElement]]
|-
|[[dom/methods/releaseCapture]]
|[[dom/document]], [[dom/Element]]
|-
|[[dom/methods/setData]], [[dom/methods/getData]], [[dom/methods/clearData]]
|[[dom/objects/dataTransfer]], [[dom/clipboardData]]
|-
|[[apis/file/methods/abort]]
|[[apis/file/FileReader]], [[apis/file/MSStreamReader]]
|-
|[[apis/audio-video/events/addtrack]]
|[[apis/audio-video/TextTrackList]]
|-
|[[dom/traversal/properties/filter]]
|[[dom/traversal/TreeWalker]] and the current one
|-
|[[dom/properties/data]]
|[[dom/objects/CompositionEvent|CompositionEvent]], [[dom/objects/MessageEvent|MessageEvent]], [[dom/objects/TextEvent|TextEvent]]
|-
|[[dom/properties/locale]]
|[[dom/objects/CompositionEvent|CompositionEvent]], [[dom/objects/KeyboardEvent|KeyboardEvent]], [[dom/objects/TextEvent|TextEvent]]
|}
*Pages on which a lot of pages depend that should be moved/renamed -
{|
! Page
! Move/Rename To
|-
|[[dom/window]]
|[[dom/Window]]
|-
|[[dom/document]]
|[[dom/Document]]
|-
|[[dom/navigator]]
|[[dom/Navigator]]
|-
|[[dom/history]]
|[[dom/History]]
|-
|[[dom/images]]
|[[dom/Image]] (?!)
|-
|[[dom/properties/children_(document)%2BB416]]
|[[dom/properties/children]]
|-
|[[dom/implementation]]
|[[dom/DOMImplementation]] (?)
|}