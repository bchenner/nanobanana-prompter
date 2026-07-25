# Image Prompt Examples

A reference library of image prompt examples organized by format type. These examples demonstrate the range of prompt structures from compact social-media-style descriptions to full analytical breakdowns with detailed object graphs.

---

## Compact Format Examples

Compact prompts use a simplified structure focused on subject, accessories, photography style, and background. Best for straightforward social media content where the scene is relatively simple.

---

### Mirror Selfie — Outfit Check

A full-body mirror selfie in a minimalist bedroom. Demonstrates compact format with detailed clothing descriptions, mirror selfie conventions, and lifestyle background elements.

```json
{
"subject": {
"description": "A young woman taking a full-body mirror selfie, one hand casually tucked into her pocket, standing in a minimalist bedroom",
"mirror_rules": "ignore mirror physics for text on clothing, display text forward and legible to viewer, no extra characters",
"age": "young adult",
"expression": "obscured by phone",
"hair": {
"color": "brunette",
"style": "shoulder-length bob, loose and casual, tucked slightly into hoodie"
},
"clothing": {
"top": {
"type": "oversized hoodie",
"color": "washed forest green",
"details": "vintage wash texture, kangaroo pocket, dropped shoulders, thick comfy fabric"
},
"bottom": {
"type": "barrel-leg trousers",
"color": "optic white",
"details": "high-waisted denim, relaxed tapered fit, slightly cropped at ankle"
},
"shoes": {
"type": "retro sneakers",
"color": "grey and teal green",
"details": "gum soles, classic three-stripe design (Adidas Samba style), white ribbed socks"
}
},
"face": {
"preserve_original": true,
"makeup": "minimal natural look (mostly hidden by phone)"
}
},
"accessories": {
"bag": {
"type": "black leather shoulder bag",
"details": "slouchy hobo style, worn over the shoulder"
},
"jewelry": {
"rings": "multiple silver/gold rings on fingers holding the phone"
},
"device": {
"type": "smartphone",
"details": "light baby blue case, covering the face"
}
},
"photography": {
"camera_style": "modern aesthetic influencer style",
"aspect_ratio": "9:16",
"angle": "standing mirror selfie",
"shot_type": "full body outfit check",
"texture": "directional natural daylight, clean minimalist aesthetic, sharp fabric details, realistic deeper shadows in background"
},
"background": {
"setting": "clean minimalist apartment bedroom",
"wall_color": "white",
"elements": [
"mid-century modern wooden chair with green cushion (left)",
"white modern drawer unit (right)",
"framed art poster with blue distorted smiley faces",
"woven jute rug",
"polished wooden floorboards"
],
"atmosphere": "cozy, stylish, clean girl aesthetic",
"lighting": "dim directional daylight entering from the left, creating a moody atmosphere with the back of the room in deep, cool-toned shadow"
}
}
```

---

### Mirror Selfie — Matcha Drink

A waist-up mirror selfie with a playful expression and iced matcha drink. Demonstrates compact format with prop interaction, layered accessories, and casual bedroom setting.

```json
{
"subject": {
"description": "A young woman taking a mirror selfie, playfully biting the straw of an iced green drink",
"mirror_rules": "ignore mirror physics for text on clothing, display text forward and legible to viewer, no extra characters",
"age": "young adult",
"expression": "playful, nose scrunched, biting straw",
"hair": {
"color": "brown",
"style": "long straight hair falling over shoulders"
},
"clothing": {
"top": {
"type": "ribbed knit cami top",
"color": "white",
"details": "cropped fit, thin straps, small dainty bow at neckline"
},
"bottom": {
"type": "denim jeans",
"color": "light wash blue",
"details": "relaxed fit, visible button fly"
}
},
"face": {
"preserve_original": true,
"makeup": "natural sunkissed look, glowing skin, nude glossy lips"
}
},
"accessories": {
"headwear": {
"type": "olive green baseball cap",
"details": "white NY logo embroidery, silver over-ear headphones worn over the cap"
},
"jewelry": {
"earrings": "large gold hoop earrings",
"necklace": "thin gold chain with cross pendant",
"wrist": "gold bangles and bracelets mixed",
"rings": "multiple gold rings"
},
"device": {
"type": "smartphone",
"details": "white case with pink floral pattern"
},
"prop": {
"type": "iced beverage",
"details": "plastic cup with iced matcha latte and green straw"
}
},
"photography": {
"camera_style": "smartphone mirror selfie aesthetic",
"angle": "eye-level mirror reflection",
"shot_type": "waist-up composition, subject positioned on the right side of the frame",
"aspect_ratio": "9:16 vertical",
"texture": "sharp focus, natural indoor lighting, social media realism, clean details"
},
"background": {
"setting": "bright casual bedroom",
"wall_color": "plain white",
"elements": [
"bed with white textured duvet",
"black woven shoulder bag lying on bed",
"leopard print throw pillow",
"distressed white vintage nightstand",
"modern bedside lamp with white shade"
],
"atmosphere": "casual lifestyle, cozy, spontaneous",
"lighting": "soft natural daylight"
}
}
```

---

### Car Selfie — Clean Girl

A close-up car selfie with a relaxed, candid expression. Demonstrates compact format for tight portrait framing, minimal clothing detail, and vehicle interior background.

```json
{
"subject": {
"description": "A young woman taking a car selfie with her hand resting on her forehead, smiling gently",
"age": "young adult",
"expression": "relaxed, candid, slight smile, hand casually touching forehead",
"hair": {
"color": "dark brown",
"style": "slicked back tight low bun with a precise middle part"
},
"clothing": {
"top": {
"type": "oversized hoodie",
"color": "light heather grey",
"details": "soft fleece fabric, relaxed fit, hood falling back"
}
},
"face": {
"preserve_original": true,
"makeup": "fresh natural 'clean girl' aesthetic, sun-kissed skin with visible freckles across nose, rosy blush, glossy pink lips, groomed brows"
}
},
"accessories": {
"eyewear": {
"type": "tortoise shell glasses",
"details": "oval/round acetate frames, stylish and intellectual vibe"
},
"earrings": {
"type": "gold ear stack",
"details": "multiple small gold huggie hoops and studs on the lobe and helix"
},
"jewelry": {
"necklace": "dainty gold chain with a tiny pendant",
"ring": "thin gold band on the ring finger"
}
},
"photography": {
"camera_style": "modern smartphone selfie",
"angle": "eye-level to slightly low angle",
"shot_type": "close-up portrait composition",
"aspect_ratio": "9:16 vertical",
"texture": "natural daylight, sharp focus on face, soft skin texture, bright window lighting, no grain"
},
"background": {
"setting": "interior of a car",
"elements": [
"dark car ceiling / panoramic sunroof",
"car seat headrest",
"seatbelt",
"car window showing bright daylight",
"blurred trees and buildings outside"
],
"atmosphere": "casual daily life, on-the-go, bright daytime vibe",
"lighting": "soft natural window light illuminating the face"
}
}
```

---

## Full Analytical Format Examples

Full analytical prompts use an expanded structure with `meta`, `global_context`, `color_palette`, `composition`, `objects` (with individual IDs), `text_ocr`, and `semantic_relationships`. Best for complex scenes with multiple objects, precise spatial relationships, and detailed environmental context.

---

### Product Selfie — Supplement Bottle (with Character Reference)

An outdoor patio selfie holding a supplement bottle. Demonstrates the analytical format with `character_reference` instruction for identity matching, product-focused `text_ocr`, and detailed object micro-details for product label accuracy.

```json
{
  "meta": {
    "image_quality": "High",
    "image_type": "Photo",
    "aspect_ratio": "9:16"
  },
  "character_reference": {
    "instruction": "Use the attached reference sheet as the absolute ground truth for the subject's facial features, skin texture, and body proportions. The output must be a 1:1 match of the character provided."
  },
  "global_context": {
    "scene_description": "An outdoor covered patio or deck area adjacent to a residential house. The background features light beige or gray vinyl siding with horizontal planks on the left. Directly behind is a large sliding glass door with a white frame. The glass reflects the outdoor environment, showing bare trees and a blue sky, as well as the interior of the house where a lit chandelier-style light fixture is visible.",
    "time_of_day": "Daytime",
    "weather_atmosphere": "Clear, serene, natural daylight",
    "lighting": {
      "source": "Natural",
      "direction": "Frontal/Diffused",
      "quality": "Soft",
      "color_temp": "Neutral"
    }
  },
  "color_palette": {
    "dominant_hex_estimates": ["#F5F5F5", "#007EA7", "#8B8B8B", "#2F2F2F", "#C4A484"],
    "accent_colors": ["Electric Cyan", "Gold", "Tortoiseshell Brown"],
    "contrast_level": "Medium"
  },
  "composition": {
    "camera_angle": "Eye-level",
    "framing": "Close-up (Selfie framing)",
    "depth_of_field": "Deep (Subject and immediate background in focus)",
    "focal_point": "The supplement bottle and the subject"
  },
  "subject": {
    "pose": {
      "body_position": "Standing",
      "gesture": "Left hand raised holding a bottle near shoulder height; Right arm extended forward out of frame suggesting a selfie capture",
      "head_angle": "Facing camera",
      "body_angle": "Frontal",
      "expression_mood": "Neutral/Calm"
    },
    "clothing": {
      "outfit_description": "A plain white hooded sweatshirt (hoodie)",
      "style": "Casual/Loungewear",
      "colors": ["White"],
      "fabric_details": ["Soft cotton fleece texture", "Ribbed cuff on left sleeve", "Drawstring hood folds"],
      "accessories": ["Tortoiseshell round eyeglasses", "Multiple small gold hoop earrings on right ear (viewer's left)", "Single cartilage gold hoop earring"]
    },
    "position_in_frame": "Center",
    "prominence": "Foreground"
  },
  "objects": [
    {
      "id": "obj_001",
      "label": "Supplement Bottle",
      "category": "Prop/Product",
      "location": "Mid-right (held by subject)",
      "prominence": "Foreground",
      "visual_attributes": {
        "color": "Translucent cyan/blue bottle with white cap",
        "texture": "Smooth plastic",
        "material": "Plastic",
        "state": "New",
        "dimensions_relative": "Hand-sized"
      },
      "micro_details": [
        "White screw-top lid with vertical ridges",
        "Label wraps around bottle",
        "Gummies visible inside through translucent plastic"
      ]
    },
    {
      "id": "obj_002",
      "label": "Sliding Glass Door",
      "category": "Architecture",
      "location": "Background Center/Right",
      "prominence": "Background",
      "visual_attributes": {
        "color": "White frame, dark reflective glass",
        "texture": "Glass/Metal",
        "material": "Glass/Vinyl",
        "state": "Clean",
        "dimensions_relative": "Large vertical structure"
      },
      "micro_details": [
        "Reflection of interior chandelier with three bulbs lit",
        "Reflection of exterior trees and sky",
        "White handle mechanism visible on frame"
      ]
    }
  ],
  "text_ocr": {
    "present": true,
    "content": [
      { "text": "goli", "location": "Blue Bottle Label", "font_style": "Sans-serif Lowercase Bold", "legibility": "Clear" },
      { "text": "NUTRITION", "location": "Blue Bottle Label (under logo)", "font_style": "Sans-serif Uppercase Small", "legibility": "Clear" },
      { "text": "ASHWAGANDHA", "location": "Blue Bottle Label (center)", "font_style": "Sans-serif Uppercase Bold", "legibility": "Clear" },
      { "text": "GUMMIES", "location": "Blue Bottle Label (under Ashwagandha)", "font_style": "Sans-serif Uppercase", "legibility": "Clear" }
    ]
  },
  "semantic_relationships": [
    "Subject is holding Supplement Bottle in left hand",
    "Subject is positioned in front of Sliding Glass Door and Vinyl Siding",
    "Sliding Glass Door reflects interior lighting and exterior trees",
    "Glasses are worn on Subject's face",
    "Earrings are attached to Subject's right ear"
  ]
}
```

---

### Coffee Shop Candid — Window Bar

A candid medium-shot of a woman sitting at a coffee shop window bar, sipping iced coffee. Demonstrates the full analytical format with 11 distinct objects, detailed spatial relationships, and mixed indoor/outdoor environmental context.

```json
{
"meta": {
"image_quality": "High",
"image_type": "Photo",
"aspect_ratio": "Vertical, 9:16",
"orientation": "Portrait"
},
"global_context": {
"scene_description": "A candid, medium-shot portrait of a woman sitting on a white stool at a wooden window bar inside a coffee shop. She is viewed in profile, facing left toward a large glass window. She is sipping from an iced coffee while holding a smartphone. The setting combines industrial chic elements (exposed rusty beam) with minimalist cafe aesthetics (white walls, dried florals). The exterior view through the window shows a street scene with a white pickup truck and a tree.",
"time_of_day": "Daytime",
"weather_atmosphere": "Clear, bright, urban casual",
"lighting": {
"source": "Natural Sunlight (Window)",
"direction": "Side-lighting (from left)",
"quality": "Soft/Diffused",
"color_temp": "Neutral to Warm"
}
},
"color_palette": {
"dominant_hex_estimates": [
"#3B2E2A",
"#6B8CA5",
"#D4B589",
"#2F3F28",
"#F2F0EB"
],
"accent_colors": [
"Deep Forest Green",
"Cognac Brown",
"Gold (Jewelry/Text)",
"Pale Pink (Shoe detail)"
],
"contrast_level": "Medium"
},
"composition": {
"camera_angle": "Low-angle (Lens below eye-level)",
"framing": "Medium-shot / Full-body sitting",
"depth_of_field": "Moderate (Foreground crisp, background slightly softened)",
"focal_point": "The subject's face and the drink"
},
"objects": [
{
"id": "obj_001",
"label": "Subject (Woman)",
"category": "Person",
"location": "Center/Right",
"prominence": "Foreground",
"visual_attributes": {
"color": "Caucasian skin tone, Blonde hair",
"texture": "Skin, Hair",
"material": "Biological",
"state": "Sitting, Drinking",
"dimensions_relative": "Dominant subject"
},
"micro_details": [
"Hair styled half-up with a beige claw clip",
"Gold sculptural hoop earring visible",
"Rosy blush makeup on cheek",
"Left hand holding phone, right hand holding straw/cup",
"Gold ring on left ring finger"
],
"pose_or_orientation": "Seated profile facing left, legs crossed",
"text_content": null
},
{
"id": "obj_002",
"label": "Leather Jacket",
"category": "Clothing",
"location": "On Subject",
"prominence": "Foreground",
"visual_attributes": {
"color": "Dark Espresso Brown",
"texture": "Smooth, slightly shiny leather",
"material": "Leather/Faux Leather",
"state": "Oversized fit",
"dimensions_relative": "Large"
},
"micro_details": [
"Silver zipper detail on left sleeve",
"Elasticized or gathered waistband/hem",
"Collared neckline",
"Natural folds and creases at elbow and waist"
],
"pose_or_orientation": "Worn",
"text_content": null
},
{
"id": "obj_003",
"label": "Jeans",
"category": "Clothing",
"location": "On Subject legs",
"prominence": "Foreground",
"visual_attributes": {
"color": "Medium Light Wash Blue",
"texture": "Denim",
"material": "Cotton/Denim",
"state": "Relaxed fit",
"dimensions_relative": "Medium"
},
"micro_details": [
"Fabric bunching at the knee due to seated position",
"Visible side seam stitching",
"Hem resting over sneakers"
],
"pose_or_orientation": "Worn",
"text_content": null
},
{
"id": "obj_004",
"label": "Sneakers",
"category": "Footwear",
"location": "Bottom Right",
"prominence": "Foreground",
"visual_attributes": {
"color": "Chocolate Brown with White stripes and Pink heel tab",
"texture": "Suede",
"material": "Suede/Rubber",
"state": "Clean, trendy",
"dimensions_relative": "Small"
},
"micro_details": [
"Three signature serrated white stripes",
"Gold foil text branding",
"Gum sole texture",
"White laces"
],
"pose_or_orientation": "On feet, resting on stool rung",
"text_content": "GAZELLE"
},
{
"id": "obj_005",
"label": "Handbag",
"category": "Accessory",
"location": "Left Center (On counter)",
"prominence": "Foreground",
"visual_attributes": {
"color": "Dark Forest Green",
"texture": "Woven/Intrecciato pattern",
"material": "Leather",
"state": "Sitting upright",
"dimensions_relative": "Medium"
},
"micro_details": [
"Curved handle shape",
"Dense weaving pattern visible",
"Slight sheen on leather strips"
],
"pose_or_orientation": "Resting on table",
"text_content": null
},
{
"id": "obj_006",
"label": "Iced Coffee",
"category": "Food/Drink",
"location": "Held by subject",
"prominence": "Foreground",
"visual_attributes": {
"color": "Beige/Tan liquid",
"texture": "Plastic cup, Liquid",
"material": "Plastic",
"state": "Full, condensation visible",
"dimensions_relative": "Small"
},
"micro_details": [
"Black straw",
"Ice cubes visible floating at top",
"Clear plastic lid",
"Subject's lips pursed around straw"
],
"pose_or_orientation": "Tilted slightly",
"text_content": null
},
{
"id": "obj_007",
"label": "Smartphone",
"category": "Electronics",
"location": "Held in left hand",
"prominence": "Foreground",
"visual_attributes": {
"color": "Silver/Gold metallic edges",
"texture": "Smooth metal/glass",
"material": "Metal/Glass",
"state": "In use",
"dimensions_relative": "Small"
},
"micro_details": [
"Rear camera bump visible",
"Reflective edge"
],
"pose_or_orientation": "Held at 45 degree angle",
"text_content": null
},
{
"id": "obj_008",
"label": "Structural Beam",
"category": "Architecture",
"location": "Just behind window frame",
"prominence": "Mid-ground",
"visual_attributes": {
"color": "Rusty Red/Brown",
"texture": "Rough, oxidized metal",
"material": "Steel/Iron",
"state": "Weathered",
"dimensions_relative": "Tall vertical"
},
"micro_details": [
"Graffiti tags/writing in black marker or paint",
"Rust patches",
"Industrial bolts or rivets at top"
],
"pose_or_orientation": "Vertical",
"text_content": "Illegible vertical tags"
},
{
"id": "obj_009",
"label": "Window Bar/Counter",
"category": "Furniture",
"location": "Bottom Left",
"prominence": "Foreground",
"visual_attributes": {
"color": "Light warm wood",
"texture": "Wood grain",
"material": "Wood",
"state": "Clean",
"dimensions_relative": "Horizontal plane"
},
"micro_details": [
"Smooth finish",
"Supports bag and subject's elbows"
],
"pose_or_orientation": "Horizontal",
"text_content": null
},
{
"id": "obj_010",
"label": "Exterior Truck",
"category": "Vehicle",
"location": "Outside Window (Background)",
"prominence": "Background",
"visual_attributes": {
"color": "White",
"texture": "Metal",
"material": "Automotive",
"state": "Parked or moving slowly",
"dimensions_relative": "Distant"
},
"micro_details": [
"Pickup bed visible",
"Black window trim",
"Logo on tailgate"
],
"pose_or_orientation": "Rear facing",
"text_content": "FORD (Blurry)"
},
{
"id": "obj_011",
"label": "Dried Floral Decor",
"category": "Decor",
"location": "Top Right Wall",
"prominence": "Background",
"visual_attributes": {
"color": "Beige/Tan/Brown",
"texture": "Dry, leafy",
"material": "Dried plants",
"state": "Mounted",
"dimensions_relative": "Medium"
},
"micro_details": [
"Palm leaf shape",
"Circular metal hoop mounting",
"Spiky texture"
],
"pose_or_orientation": "Wall mounted",
"text_content": null
}
],
"text_ocr": {
"present": true,
"content": [
{
"text": "GAZELLE",
"location": "Side of brown sneaker",
"font_style": "Sans-serif, gold foil",
"legibility": "Clear"
},
{
"text": "FORD",
"location": "Tailgate of white truck outside",
"font_style": "Bold, uppercase",
"legibility": "Partially obscured/Blurry"
}
]
},
"semantic_relationships": [
"Subject is sitting on the White Stool",
"Subject is holding Iced Coffee and Smartphone",
"Subject is leaning on Window Bar",
"Handbag is resting on Window Bar next to Subject",
"Window Bar is adjacent to Large Window",
"Large Window reveals Exterior Truck and Tree",
"Structural Beam is vertically transecting the window view",
"Dried Floral Decor is mounted on the white wall behind Subject"
]
}
```

---

### Mirror Selfie — Retail Store

A full-body mirror selfie in a high-end retail store. Demonstrates the analytical format with streetwear styling, industrial-chic architecture, and layered accessory details across 10 objects.

```json
{
"meta": {
"image_quality": "High",
"image_type": "Photo",
"resolution_estimation": "Vertical 9:16 aspect ratio"
},
"global_context": {
"scene_description": "A full-body mirror selfie captured indoors, positioned centrally within a high-end retail store environment. The subject is a female wearing streetwear, specifically a distressed brown leather jacket, cream knit scarf wrapped as a balaclava, and white split-toe boots. The setting features industrial-chic design elements: grey terrazzo flooring, fluted metallic columns, and white display pedestals. A background arched mirror reflects the store's depth and a second individual.",
"time_of_day": "Indeterminate (Interior Artificial)",
"weather_atmosphere": "Climate-controlled/Retail/Minimalist",
"lighting": {
"source": "Artificial",
"direction": "Overhead/Diffused",
"quality": "Soft/Even",
"color_temp": "Neutral White"
}
},
"color_palette": {
"dominant_hex_estimates": [
"#3E342F",
"#F0EFE8",
"#1C1C1C",
"#9EA0A3",
"#CFCFCF"
],
"accent_colors": [
"Olive Drab (Cuffs)",
"Metallic Silver (Columns)",
"Bright White (Logo)"
],
"contrast_level": "Medium"
},
"composition": {
"camera_angle": "Eye-level (Mirror reflection)",
"framing": "Full-body vertical",
"depth_of_field": "Deep",
"focal_point": "Subject's face and scarf framing"
},
"objects": [
{
"id": "obj_001",
"label": "Main Subject",
"category": "Person",
"location": "Center",
"prominence": "Foreground",
"visual_attributes": {
"color": "N/A",
"texture": "Skin/Fabric mix",
"material": "Biological/Textile",
"state": "Posing",
"dimensions_relative": "Vertical span approx 85%"
},
"micro_details": [
"Right hand touching chin",
"Pouting expression",
"Silver rings on multiple fingers",
"Gaze directed at phone screen"
],
"pose_or_orientation": "Standing facing forward",
"text_content": null
},
{
"id": "obj_002",
"label": "Leather Jacket",
"category": "Clothing",
"location": "Torso",
"prominence": "Foreground",
"visual_attributes": {
"color": "Distressed Brown",
"texture": "Leathery/Creased",
"material": "Leather",
"state": "Vintage/Worn",
"dimensions_relative": "Oversized/Boxy"
},
"micro_details": [
"Ribbed olive green cuffs",
"Visible zipper placket",
"Elastic waistband",
"Natural wear patterns on sleeves"
],
"pose_or_orientation": "Worn on body",
"text_content": null
},
{
"id": "obj_003",
"label": "Knit Scarf",
"category": "Accessory",
"location": "Head/Neck",
"prominence": "Foreground",
"visual_attributes": {
"color": "Cream/Ecru",
"texture": "Fuzzy/Ribbed knit",
"material": "Mohair or Wool blend",
"state": "Clean",
"dimensions_relative": "Large volume"
},
"micro_details": [
"Wrapped hood-style over cap",
"Long fringe tassels hanging centrally",
"Soft texture visible against leather"
],
"pose_or_orientation": "Draped",
"text_content": null
},
{
"id": "obj_004",
"label": "Baseball Cap",
"category": "Accessory",
"location": "Head",
"prominence": "Foreground",
"visual_attributes": {
"color": "Chocolate Brown",
"texture": "Canvas/Twill",
"material": "Cotton",
"state": "New",
"dimensions_relative": "Standard"
},
"micro_details": [
"White embroidered logo",
"Curved brim",
"Partially covered by scarf"
],
"pose_or_orientation": "Worn on head",
"text_content": "Stylized 'P' or 'f'"
},
{
"id": "obj_005",
"label": "Baggy Trousers",
"category": "Clothing",
"location": "Legs",
"prominence": "Foreground",
"visual_attributes": {
"color": "Black",
"texture": "Matte fabric",
"material": "Denim or Canvas",
"state": "Clean",
"dimensions_relative": "Wide silhouette"
},
"micro_details": [
"Pooling slightly at ankles",
"Fabric folds near knees",
"Deep black tone absorbs detail"
],
"pose_or_orientation": "Worn on legs",
"text_content": null
},
{
"id": "obj_006",
"label": "Tabi Boots",
"category": "Footwear",
"location": "Feet",
"prominence": "Foreground",
"visual_attributes": {
"color": "White/Bone",
"texture": "Smooth leather",
"material": "Leather",
"state": "Clean",
"dimensions_relative": "Standard"
},
"micro_details": [
"Split-toe detail clearly visible",
"Rounded heel geometry",
"Contrast against grey floor"
],
"pose_or_orientation": "Standing",
"text_content": null
},
{
"id": "obj_007",
"label": "iPhone Pro",
"category": "Electronics",
"location": "Hand",
"prominence": "Foreground",
"visual_attributes": {
"color": "Graphite/Black",
"texture": "Glass/Metal",
"material": "Composite",
"state": "Active",
"dimensions_relative": "Standard"
},
"micro_details": [
"Triple lens array",
"Magsafe ring hint",
"Reflecting overhead light"
],
"pose_or_orientation": "Vertical",
"text_content": null
},
{
"id": "obj_008",
"label": "Terrazzo Flooring",
"category": "Architecture",
"location": "Floor",
"prominence": "Background",
"visual_attributes": {
"color": "Grey aggregate",
"texture": "Polished stone",
"material": "Concrete/Stone",
"state": "Polished",
"dimensions_relative": "Expansive"
},
"micro_details": [
"Speckled pattern",
"Tile grout lines",
"Reflective sheen"
],
"pose_or_orientation": "Horizontal",
"text_content": null
},
{
"id": "obj_009",
"label": "Fluted Columns",
"category": "Architecture",
"location": "Background Walls",
"prominence": "Background",
"visual_attributes": {
"color": "Silver/Grey",
"texture": "Vertical Ridges",
"material": "Metal/Plaster",
"state": "Fixed",
"dimensions_relative": "Floor-to-ceiling"
},
"micro_details": [
"Shadow lines in fluting",
"Industrial aesthetic",
"Symmetrical placement"
],
"pose_or_orientation": "Vertical",
"text_content": null
},
{
"id": "obj_010",
"label": "Background Mirror",
"category": "Fixture",
"location": "Rear Wall",
"prominence": "Background",
"visual_attributes": {
"color": "Silver",
"texture": "Reflective",
"material": "Glass",
"state": "Clean",
"dimensions_relative": "Large Arched"
},
"micro_details": [
"Reflects secondary person",
"Reflects rear store lighting",
"Arched top edge"
],
"pose_or_orientation": "Vertical",
"text_content": null
}
],
"text_ocr": {
"present": true,
"content": [
{
"text": "P",
"location": "Cap front",
"font_style": "Gothic/Blackletter",
"legibility": "Clear"
}
]
},
"semantic_relationships": [
"Subject holding iPhone obscures center torso",
"Scarf draped over Head covers Cap partially",
"Boots standing on Terrazzo Floor",
"Mirror Background reflects Secondary Person behind Subject"
]
}
```

---

### Alpine Breakfast — Scenic Balcony

A scenic breakfast scene on a high-altitude alpine balcony. Demonstrates the analytical format at scale with 14 objects spanning food items, furniture, architecture, and natural landscape elements. Shows how to handle deep background layering from foreground table through mid-ground railing to distant mountains.

```json
{
"meta": {
"image_quality": "High",
"image_type": "Photo",
"resolution_estimation": "High definition, likely smartphone or DSLR portrait"
},
"global_context": {
"scene_description": "A first-person perspective or just-behind-subject shot of a scenic breakfast on a high-altitude balcony. A woman sits facing away from the camera, looking out over a lush alpine valley (resembling the Swiss Alps, likely Lauterbrunnen/Wengen area) towards massive snow-capped mountains. The foreground is dominated by a breakfast spread on a round table and the woman in white loungewear. The background features deep green valleys, pine forests, alpine chalets, and towering rock faces under a textured blue sky.",
"time_of_day": "Morning",
"weather_atmosphere": "Serene, Clear with textured clouds, Fresh",
"lighting": {
"source": "Sunlight",
"direction": "From the left/East (casting soft shadows to the right)",
"quality": "Soft but bright morning light",
"color_temp": "Cool daylight with warm highlights"
}
},
"color_palette": {
"dominant_hex_estimates": ["#5A6E8C", "#2F4F2F", "#F2F2F0", "#3E2B26", "#8CB8D9"],
"accent_colors": ["Geranium Pink", "Egg Yolk Yellow", "Terracotta (Roofs)", "Orange Juice Amber"],
"contrast_level": "Medium-High"
},
"composition": {
"aspect_ratio": "Vertical, 9:16",
"camera_angle": "Eye-level (slightly elevated above table)",
"framing": "Medium-shot vertical",
"depth_of_field": "Deep (Foreground objects are sharp, background mountains remain relatively distinct)",
"focal_point": "The woman gazing at the mountains, guiding the viewer's eye to the landscape"
},
"objects": [
{"id": "obj_001", "label": "Woman", "category": "Person", "location": "Bottom Right Quadrant", "prominence": "Foreground", "visual_attributes": {"color": "White/Cream outfit, Dark Brown hair", "texture": "Cotton fabric, smooth skin, silky hair", "material": "Textile, Organic", "state": "Relaxed", "dimensions_relative": "Occupies roughly 25% of the lower frame"}, "micro_details": ["Hair tied back in a low ponytail", "Wearing a short-sleeved white t-shirt", "Wearing loose-fitting white trousers", "Silver bracelet visible on left wrist", "Left hand resting gently on left knee", "Knees drawn up slightly", "Profile of right cheek and ear visible"], "pose_or_orientation": "Seated, facing away (3/4 rear view), head turned slightly right", "text_content": null},
{"id": "obj_002", "label": "Breakfast Table", "category": "Furniture", "location": "Bottom Left Quadrant", "prominence": "Foreground", "visual_attributes": {"color": "Dark Brown/Black", "texture": "Smooth, matte", "material": "Wood or Composite", "state": "Set for meal", "dimensions_relative": "Medium circular surface"}, "micro_details": ["Tripod style legs visible", "Surface reflects diffuse light from the sky", "Occupied by multiple dishes"], "pose_or_orientation": "Stationary", "text_content": null},
{"id": "obj_003", "label": "Wicker Chair", "category": "Furniture", "location": "Bottom Right", "prominence": "Foreground", "visual_attributes": {"color": "Dark Brown/Black", "texture": "Woven/Wicker pattern", "material": "Synthetic Rattan or Wicker", "state": "Occupied", "dimensions_relative": "Standard chair size"}, "micro_details": ["Woven texture visible on the backrest", "Angular armrest"], "pose_or_orientation": "Facing left/into the scene", "text_content": null},
{"id": "obj_004", "label": "Plate of Eggs (Left)", "category": "Food/Crockery", "location": "Table Left", "prominence": "Foreground", "visual_attributes": {"color": "White plate, Yellow eggs", "texture": "Ceramic smooth, fluffy food", "material": "Ceramic, Organic", "state": "Served", "dimensions_relative": "Small dinner plate"}, "micro_details": ["Scrambled eggs", "Silver fork resting on napkin beside plate", "Shadow cast by the plate onto table"], "pose_or_orientation": "Flat on table", "text_content": null},
{"id": "obj_005", "label": "Plate of Breakfast (Right)", "category": "Food/Crockery", "location": "Table Right (near woman)", "prominence": "Foreground", "visual_attributes": {"color": "White plate, Red/Brown/Yellow food", "texture": "Mixed", "material": "Ceramic, Organic", "state": "Served", "dimensions_relative": "Small dinner plate"}, "micro_details": ["Appears to be an omelet or quiche", "Grilled tomato half", "Slice of bacon or sausage", "Knife resting on rim"], "pose_or_orientation": "Flat on table", "text_content": null},
{"id": "obj_006", "label": "Toast Selection", "category": "Food", "location": "Table Top Left", "prominence": "Foreground", "visual_attributes": {"color": "Golden Brown toast, White plate", "texture": "Crisp", "material": "Bread", "state": "Toasted", "dimensions_relative": "Small grouping"}, "micro_details": ["Two distinct slices of toast", "Small jar of jam (dark red/purple) nearby", "Small butter packet/container"], "pose_or_orientation": "Stacked", "text_content": null},
{"id": "obj_007", "label": "Orange Juice", "category": "Beverage", "location": "Table Center-Left", "prominence": "Foreground", "visual_attributes": {"color": "Vibrant Orange", "texture": "Liquid", "material": "Glass container", "state": "Full", "dimensions_relative": "Short tumbler"}, "micro_details": ["Surface liquid line visible", "Pulp texture suggested by opacity"], "pose_or_orientation": "Upright", "text_content": null},
{"id": "obj_008", "label": "Milk Jug/Coffee Pot", "category": "Crockery", "location": "Table Center", "prominence": "Foreground", "visual_attributes": {"color": "White", "texture": "Glossy Ceramic", "material": "Porcelain", "state": "Closed/Upright", "dimensions_relative": "Small pitcher"}, "micro_details": ["Spout visible", "Lid present", "Reflective highlight on curve"], "pose_or_orientation": "Upright", "text_content": null},
{"id": "obj_009", "label": "Coffee Cup", "category": "Crockery", "location": "Table Foreground Center", "prominence": "Foreground", "visual_attributes": {"color": "White", "texture": "Ceramic", "material": "Porcelain", "state": "Empty or containing dark liquid", "dimensions_relative": "Standard cup"}, "micro_details": ["Resting on saucer", "Spoon handle visible on saucer", "Handle oriented to the right"], "pose_or_orientation": "Upright", "text_content": null},
{"id": "obj_010", "label": "Balcony Railing", "category": "Architecture", "location": "Mid-ground (horizontally across)", "prominence": "Mid-ground", "visual_attributes": {"color": "Weathered Wood Brown", "texture": "Wood grain", "material": "Wood", "state": "Structural", "dimensions_relative": "Spans width of image"}, "micro_details": ["Wide top beam", "Vertical slats below", "Metal brackets barely visible"], "pose_or_orientation": "Horizontal", "text_content": null},
{"id": "obj_011", "label": "Flower Box", "category": "Plant", "location": "Attached to Railing (Center)", "prominence": "Mid-ground", "visual_attributes": {"color": "Pink flowers, Green leaves", "texture": "Organic", "material": "Geraniums", "state": "Blooming", "dimensions_relative": "Cluster"}, "micro_details": ["Small pink petals", "Dense green foliage", "Overhanging the railing slightly"], "pose_or_orientation": "Growing upward/outward", "text_content": null},
{"id": "obj_012", "label": "Valley Village", "category": "Architecture", "location": "Mid-ground/Background (lower valley)", "prominence": "Background", "visual_attributes": {"color": "Brown roofs, White walls", "texture": "Distance-blurred", "material": "Stone/Wood", "state": "Settled", "dimensions_relative": "Tiny due to distance"}, "micro_details": ["Classic Alpine chalet architecture", "Sloped roofs for snow", "Scattered layout among trees"], "pose_or_orientation": "Static", "text_content": null},
{"id": "obj_013", "label": "Mountain Range", "category": "Nature", "location": "Background", "prominence": "Background", "visual_attributes": {"color": "Grey rock, White snow, Green slopes", "texture": "Rugged, Rocky", "material": "Granite/Limestone/Ice", "state": "Permanent", "dimensions_relative": "Massive"}, "micro_details": ["Snow caps on highest peaks", "Sheer vertical cliff faces (typical of glaciated valleys)", "Shadows defining the ridges", "Atmospheric haze softening the most distant peaks"], "pose_or_orientation": "Vertical rise", "text_content": null},
{"id": "obj_014", "label": "Sky", "category": "Nature", "location": "Top third", "prominence": "Background", "visual_attributes": {"color": "Azure Blue, White clouds", "texture": "Cloudy/Wispy", "material": "Gas/Vapor", "state": "Moving", "dimensions_relative": "Expansive"}, "micro_details": ["Altocumulus or Stratocumulus cloud formation (mackerel sky)", "Small patches of clear blue visible between clouds", "Clouds are denser towards the horizon"], "pose_or_orientation": "Overhead", "text_content": null}
],
"text_ocr": {
"present": false,
"content": []
},
"semantic_relationships": [
"The woman is looking at the Mountain Range",
"The Breakfast Table is positioned in front of the Woman",
"The Balcony Railing separates the immediate foreground from the Valley Village",
"The Flower Box is mounted on the Balcony Railing",
"The Mountains frame the Valley Village",
"Sunlight is illuminating the left side of the Woman's face and the Table"
]
}
```

---

### Private Jet Portrait

> **Note:** This example is truncated. Only the `meta` and `global_context` sections were available. It demonstrates the opening structure for a luxury interior scene with mixed lighting sources.

A portrait inside a private aircraft cabin. Shows how to handle enclosed luxury environments with mixed artificial and natural lighting.

```json
{
"meta": {
"image_quality": "Medium-High",
"image_type": "Photograph/Social Media Portrait",
"resolution_estimation": "Vertical aspect ratio (approx 9:16)"
},
"global_context": {
"scene_description": "The interior of a private aircraft cabin featuring a female subject seated in a luxury leather captain's chair. The cabin is finished with high-gloss dark wood veneers and cream-colored upholstery. The subject is engaged in a phone conversation while looking away from the camera. The setting conveys opulence and travel.",
"time_of_day": "Daytime",
"weather_atmosphere": "Serene, enclosed, artificial environment with exterior daylight",
"lighting": {
"source": "Mixed",
"direction": "Side lighting from windows (left) and ambient warm overhead cove lighting",
"quality": "Soft, diffused interior light with specular highlights on glossy surfaces",
"color_temp": "Warm (interior) / Neutral (daylight)"
}
}
}
```

---

### Bedroom Mirror Selfie — Pink Striped Shirt

A mirror selfie in a bright bedroom featuring a pink striped shirt and flower hair clip. Demonstrates the analytical format with asymmetrical composition analysis, backlit lighting, and 9 objects including architectural elements like windows and radiators.

```json
{
"meta": {
"image_quality": "Medium-High",
"image_type": "Photograph/Social Media Portrait",
"resolution_estimation": "Vertical aspect ratio (approx 9:16)"
},
"global_context": {
"scene_description": "A mirror selfie captured in a bright bedroom. The composition is asymmetrical: the subject (a person) occupies the right half of the frame, facing away from the viewer towards a mirror. Their left hand holds a smartphone near the vertical center line, capturing the reflection. The left side of the image reveals the background room environment, including a window and radiator. The right side is dominated by the subject's pink striped shirt and hairstyle.",
"time_of_day": "Daytime",
"weather_atmosphere": "Bright/Clear",
"lighting": {
"source": "Natural daylight (primary) mixed with ambient indoor reflection",
"direction": "Backlit (light entering from window behind the subject)",
"quality": "Diffused/Soft",
"color_temp": "Neutral leaning cool (daylight)"
}
},
"color_palette": {
"dominant_hex_estimates": [
"#E8D8D8",
"#FFFFFF",
"#A08070",
"#B0C4B0"
],
"accent_colors": [
"Pastel Pink",
"Cream/Yellow (Hair clip)",
"Dark Brown (Bag)",
"Leafy Green (Window view)"
],
"contrast_level": "Medium"
},
"composition": {
"camera_angle": "Eye-level (reflected)",
"framing": "Medium-shot / Asymmetrical composition",
"depth_of_field": "Deep",
"focal_point": "The hair clip (Right) and smartphone (Center-Left)"
},
"objects": [
{
"id": "obj_001",
"label": "Person (Subject)",
"category": "Person",
"location": "Right side of frame / Right-of-center",
"prominence": "Primary Subject",
"visual_attributes": {
"color": "Skin tone visible on neck/hand, Hair is brown/dark blonde",
"texture": "Skin smooth, Hair textured/messy bun",
"material": "Biological",
"state": "Posed",
"dimensions_relative": "Occupies the right 50-60% of the frame width"
},
"micro_details": [
"Messy bun hairstyle with loose strands near nape and ears",
"Left hand gripping phone",
"Gold hoop earring visible on left ear",
"Manicured fingernails with white tips or solid light color",
"Gold ring bands visible on fingers of left hand"
],
"pose_or_orientation": "Standing on the right, angled towards the mirror",
"text_content": null
},
{
"id": "obj_002",
"label": "Shirt",
"category": "Clothing",
"location": "Bottom Right Quadrant",
"prominence": "Foreground",
"visual_attributes": {
"color": "Pastel pink and white vertical stripes",
"texture": "Cotton/Poplin fabric weave",
"material": "Fabric",
"state": "Worn, draped loosely",
"dimensions_relative": "Dominated the lower right frame"
},
"micro_details": [
"Vertical stripe pattern",
"Cuff visible on left sleeve",
"Collar folded",
"Loose/oversized fit",
"Folds and shadows indicating fabric drape"
],
"pose_or_orientation": "Worn on body",
"text_content": null
},
{
"id": "obj_003",
"label": "Hair Clip",
"category": "Accessory",
"location": "Upper Right Quadrant",
"prominence": "Focal Highlight",
"visual_attributes": {
"color": "Cream with yellow center gradient",
"texture": "Smooth plastic/acetate",
"material": "Plastic",
"state": "Functional/Holding hair",
"dimensions_relative": "Small but distinct"
},
"micro_details": [
"Flower shape (resembling a Plumeria/Frangipani)",
"Claw mechanism visible gripping hair bun",
"Glossy finish reflecting light"
],
"pose_or_orientation": "Attached to hair on the right",
"text_content": null
},
{
"id": "obj_004",
"label": "Smartphone",
"category": "Device",
"location": "Center-Left (dividing line)",
"prominence": "Foreground",
"visual_attributes": {
"color": "Beige/Clay case",
"texture": "Matte case, Glass lenses",
"material": "Plastic/Silicone/Glass",
"state": "Active (taking photo)",
"dimensions_relative": "Standard smartphone size"
},
"micro_details": [
"Three camera lenses (Pro model arrangement)",
"Flash module visible",
"Fingers wrapped around edges",
"Case color matches aesthetic palette"
],
"pose_or_orientation": "Held vertically, lens facing mirror",
"text_content": null
},
{
"id": "obj_005",
"label": "Ceiling Light",
"category": "Fixture",
"location": "Top Left Corner",
"prominence": "Background",
"visual_attributes": {
"color": "White",
"texture": "Paper/Rice paper",
"material": "Paper",
"state": "Hanging",
"dimensions_relative": "Large sphere"
},
"micro_details": [
"Wire frame structure faintly visible inside",
"Spherical shape",
"Suspended by white cord"
],
"pose_or_orientation": "Hanging from ceiling",
"text_content": null
},
{
"id": "obj_006",
"label": "Window",
"category": "Architecture",
"location": "Background Left",
"prominence": "Background",
"visual_attributes": {
"color": "White frame, Green exterior view",
"texture": "Glass, Painted wood/uPVC",
"material": "Glass/Frame",
"state": "Closed",
"dimensions_relative": "Large rectangular"
},
"micro_details": [
"Muntin bars dividing panes",
"Green foliage visible outside (trees/bushes)",
"Bright daylight entering"
],
"pose_or_orientation": "Vertical wall mount",
"text_content": null
},
{
"id": "obj_007",
"label": "Radiator",
"category": "Fixture",
"location": "Background Left (below window)",
"prominence": "Background",
"visual_attributes": {
"color": "White",
"texture": "Metal/Enamel",
"material": "Metal",
"state": "Fixed",
"dimensions_relative": "Standard width"
},
"micro_details": [
"Horizontal ridges",
"Located directly under window sill"
],
"pose_or_orientation": "Mounted to wall",
"text_content": null
},
{
"id": "obj_008",
"label": "Tote Bag",
"category": "Accessory",
"location": "Bottom Left (Background)",
"prominence": "Background clutter",
"visual_attributes": {
"color": "Dark Brown/Black with pattern",
"texture": "Coated canvas/Leather",
"material": "Synthetic/Leather",
"state": "Hanging/Resting",
"dimensions_relative": "Medium"
},
"micro_details": [
"Checkered/geometric pattern visible",
"Handles visible",
"Slouching shape"
],
"pose_or_orientation": "Hanging low",
"text_content": null
},
{
"id": "obj_009",
"label": "Bedding",
"category": "Furniture/Textile",
"location": "Bottom Right Edge",
"prominence": "Foreground/Background edge",
"visual_attributes": {
"color": "Cream/White",
"texture": "Boucle/Sherpa fleece (highly textured)",
"material": "Fabric",
"state": "Soft",
"dimensions_relative": "Partial view"
},
"micro_details": [
"High pile texture",
"Rounded edge of bed/pillow"
],
"pose_or_orientation": "Stationary",
"text_content": null
}
],
"text_ocr": {
"present": false,
"content": []
},
"semantic_relationships": [
"Subject (obj_001) is positioned on the right, holding Smartphone (obj_004)",
"Smartphone (obj_004) divides the visual field between the open room (Left) and the subject (Right)",
"Hair Clip (obj_003) is on the rightmost edge of the subject's silhouette",
"Window (obj_006) provides light from the left side relative to the reflected image",
"Radiator (obj_007) and Tote Bag (obj_008) occupy the empty space on the left"
]
}
```
