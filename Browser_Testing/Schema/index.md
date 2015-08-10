---
title: WPD:Browser Testing/Schema
path: Browser_Testing/Schema

---
<p>Here is a sample schema:
</p><p><i><b>Note:</b> this schema does not yet take into account different support statuses per OS for each browser.</i>
</p><p><br />
</p>
<pre class="language-html5" data-lang="html5">
{
   "features"&#160;: {
      "(feature-name)": {
         "category": "(CSS, HTML, API, DOM, MathML, JS, ...)",
         "type": "(property, method, ...)",
         "stats": {
            "(sub-feature)": {
               "(ua-string)": {
                  "(version-number)": "support code",
                  "(Supported / Prefix)": "(prefix)"
               }
            }
         },
         "notes": {
            "(ua-string)": {
               "(version-number)": "note"
            }            
         }
      },
      "border-radius": {
         "category": "CSS",
         "type": "property",
         "stats": {
            "Basic Support": {
               "chrome": {
                  "4.0": "y",
                  "0.2": "prefix (or -webkit)"
               },
               "firefox": {
                  "4.0 (2.0)": "y",
                  "1.0 (1.7 or earlier)": "prefix (or -moz)"
               },
               "ie": {
                  "9.0": "y"
               },
               "opera": {
                  "10.5": "y"
               },
               "safari": {
                  "5.0": "y",
                  "3.0": "prefix (or -webkit)"
               }
            },
            "Percentages": {
               "chrome": {
                  "Supported": "y"
               },
               "firefox": {
                  "4": "y"
               },
               "ie": {
                  "9": "y"
               },
               "opera": {
                  "11.5": "y"
               },
               "safari": {
                  "5.1": "y"
               }
            },
            "Elliptical borders": {
               "chrome": {
                  "Supported": "y"
               },
               "firefox": {
                  "3.5 (1.9.1)": "y",
                  "Supported prefix": "prefix (or -moz)"
               },
               "ie": {
                  "9": "y"
               },
               "opera": {
                  "Supported": "y"
               },
               "safari": {
                  "Supported": "y"
               }
            },
            "4 values for 4 corners": {
               "chrome": {
                  "4.0": "y",
                  "Supported prefix": "prefix (or -webkit)"
               },
               "firefox": {
                  "Supported": "y",
                  "Supported prefix": "prefix (or -moz)"
               },
               "ie": {
                  "9": "y"
               },
               "opera": {
                  "Supported": "y"
               },
               "safari": {
                  "5.0": "y"
               }
            }
         },
         "notes": {
            "firefox": {
               "3.6": "Used to treat percentage values as percentages of the width, for both axes",
               "3.6": "Non-standard longhand names (-moz-border-radius-topleft etc)"
            },   
            "webkit": {
               "532.5": "Supports only one value in border-radius. For different radii, the longhands need to be used. don't support the slash / notation. If two values are specified, they are interpreted as horizontal and vertical radii for all four corners.",
               "532.5": "When the sum of two adjacent radii exceeds the length of the side they’re on, they are reduced to 0 instead of shrinking proportionally."
            },
            "opera": {
               "11.6": "border-radius has no effect in replaced elements (like images)",
               "11.6": "Percentages are accepted in border-radius, but are treated incorrectly."
            }  
         }
      }
   }
}
</pre>

<!-- Saved in parser cache with key wpwiki:pcache:idhash:8150-0!*!*!*!*!*!*!esi=1 and timestamp 20150810200019 and revision id 31236
 -->
