---
title: WPD:Browser Testing/Schema
---
<p>Here is a sample schema:
</p><p><i><b>Note:</b> this schema does not yet take into account different support statuses per OS for each browser.</i>
</p>
<div dir="ltr" class="mw-geshi mw-code mw-content-ltr"><div class="html5 source-html5"><pre class="de1">{
   &quot;features&quot;&#160;: {
      &quot;(feature-name)&quot;: {
         &quot;category&quot;: &quot;(CSS, HTML, API, DOM, MathML, JS, ...)&quot;,
         &quot;type&quot;: &quot;(property, method, ...)&quot;,
         &quot;stats&quot;: {
            &quot;(sub-feature)&quot;: {
               &quot;(ua-string)&quot;: {
                  &quot;(version-number)&quot;: &quot;support code&quot;,
                  &quot;(Supported / Prefix)&quot;: &quot;(prefix)&quot;
               }
            }
         },
         &quot;notes&quot;: {
            &quot;(ua-string)&quot;: {
               &quot;(version-number)&quot;: &quot;note&quot;
            }            
         }
      },
      &quot;border-radius&quot;: {
         &quot;category&quot;: &quot;CSS&quot;,
         &quot;type&quot;: &quot;property&quot;,
         &quot;stats&quot;: {
            &quot;Basic Support&quot;: {
               &quot;chrome&quot;: {
                  &quot;4.0&quot;: &quot;y&quot;,
                  &quot;0.2&quot;: &quot;prefix (or -webkit)&quot;
               },
               &quot;firefox&quot;: {
                  &quot;4.0 (2.0)&quot;: &quot;y&quot;,
                  &quot;1.0 (1.7 or earlier)&quot;: &quot;prefix (or -moz)&quot;
               },
               &quot;ie&quot;: {
                  &quot;9.0&quot;: &quot;y&quot;
               },
               &quot;opera&quot;: {
                  &quot;10.5&quot;: &quot;y&quot;
               },
               &quot;safari&quot;: {
                  &quot;5.0&quot;: &quot;y&quot;,
                  &quot;3.0&quot;: &quot;prefix (or -webkit)&quot;
               }
            },
            &quot;Percentages&quot;: {
               &quot;chrome&quot;: {
                  &quot;Supported&quot;: &quot;y&quot;
               },
               &quot;firefox&quot;: {
                  &quot;4&quot;: &quot;y&quot;
               },
               &quot;ie&quot;: {
                  &quot;9&quot;: &quot;y&quot;
               },
               &quot;opera&quot;: {
                  &quot;11.5&quot;: &quot;y&quot;
               },
               &quot;safari&quot;: {
                  &quot;5.1&quot;: &quot;y&quot;
               }
            },
            &quot;Elliptical borders&quot;: {
               &quot;chrome&quot;: {
                  &quot;Supported&quot;: &quot;y&quot;
               },
               &quot;firefox&quot;: {
                  &quot;3.5 (1.9.1)&quot;: &quot;y&quot;,
                  &quot;Supported prefix&quot;: &quot;prefix (or -moz)&quot;
               },
               &quot;ie&quot;: {
                  &quot;9&quot;: &quot;y&quot;
               },
               &quot;opera&quot;: {
                  &quot;Supported&quot;: &quot;y&quot;
               },
               &quot;safari&quot;: {
                  &quot;Supported&quot;: &quot;y&quot;
               }
            },
            &quot;4 values for 4 corners&quot;: {
               &quot;chrome&quot;: {
                  &quot;4.0&quot;: &quot;y&quot;,
                  &quot;Supported prefix&quot;: &quot;prefix (or -webkit)&quot;
               },
               &quot;firefox&quot;: {
                  &quot;Supported&quot;: &quot;y&quot;,
                  &quot;Supported prefix&quot;: &quot;prefix (or -moz)&quot;
               },
               &quot;ie&quot;: {
                  &quot;9&quot;: &quot;y&quot;
               },
               &quot;opera&quot;: {
                  &quot;Supported&quot;: &quot;y&quot;
               },
               &quot;safari&quot;: {
                  &quot;5.0&quot;: &quot;y&quot;
               }
            }
         },
         &quot;notes&quot;: {
            &quot;firefox&quot;: {
               &quot;3.6&quot;: &quot;Used to treat percentage values as percentages of the width, for both axes&quot;,
               &quot;3.6&quot;: &quot;Non-standard longhand names (-moz-border-radius-topleft etc)&quot;
            },   
            &quot;webkit&quot;: {
               &quot;532.5&quot;: &quot;Supports only one value in border-radius. For different radii, the longhands need to be used. don't support the slash / notation. If two values are specified, they are interpreted as horizontal and vertical radii for all four corners.&quot;,
               &quot;532.5&quot;: &quot;When the sum of two adjacent radii exceeds the length of the side they’re on, they are reduced to 0 instead of shrinking proportionally.&quot;
            },
            &quot;opera&quot;: {
               &quot;11.6&quot;: &quot;border-radius has no effect in replaced elements (like images)&quot;,
               &quot;11.6&quot;: &quot;Percentages are accepted in border-radius, but are treated incorrectly.&quot;
            }  
         }
      }
   }
}</pre></div></div>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:8150-0!*!*!*!*!*!*!esi=1 and timestamp 20150731184035 and revision id 31236
 -->
