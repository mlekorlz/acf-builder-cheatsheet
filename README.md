# PHP Storm Live Templates + Cheatsheet for ACF Builder

Archive contains a set of Live Templates created to speed up writing ACF Builder code.  
[PhpStorm Live Templates import guide](https://www.jetbrains.com/help/phpstorm/sharing-live-templates.html#import)

Structure for Live Template abbreviation is:
```acf``` + ```field_name``` + ```x```  
Where:  
* ```acf``` is required  
* ```field_name``` is ACF Field Type name in lowercase and no spaces ( eg. ```text```, ```relationship```, ```datetimepicker``` or ```googlemap```)  
* ```x``` is optional and output full code for chosen field  

```acftext``` outputs:
```php
->addText('text_field', [ 
    'label' => 'Text field' 
])
```

```acftextx``` outputs:
```php
->addText('text_field', [
    'label' => 'Text Field',
    'instructions' => '',
    'required' => 0,
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'default_value' => '',
    'placeholder' => '',
    'prepend' => '',
    'append' => '',
    'maxlength' => '',
])
```
etc...

This cheatsheet consists of ACF Field Type arguments for use with [ACF Builder](https://github.com/StoutLogic/acf-builder/) as well as the known (most of which are not documented) configuration methods to assist in building fields. While the below field types reveal all of the possible configuration passable in the field type config array, most have available chainable methods to assist in building out cleaner, more readable code.

If you are new to ACF Builder and would like to learn more, you can read my guide [here](https://roots.io/guides/using-acf-builder-with-sage/).

## Table of Contents

| [Basic](#basic)       | [Content](#content) | [Choice](#choice)            | [Relational](#relational)     | [jQuery](#jquery)                     | [Layout](#layout)                     | [Configuration](#configuration)   |
|:----------------------|:--------------------|:-----------------------------|:------------------------------|:--------------------------------------|:--------------------------------------|:----------------------------------|
| [Text](#text)         | [Wysiwyg](#wysiwyg) | [Select](#select)            | [Link](#link)                 | [Google Map](#google-map)             | [Message](#message)                   | [Composing](#composing-fields)    |
| [Textarea](#textarea) | [Oembed](#oembed)   | [Checkbox](#checkbox)        | [Post Object](#post-object)   | [Date Picker](#date-picker)           | [Accordion](#accordion)               | [Modifying](#modifying-fields)    |
| [Number](#number)     | [Image](#image)     | [Radio](#radio)              | [Page Link](#page-link)       | [Date Time Picker](#date-time-picker) | [Tab](#tab)                           | [Removing](#removing-fields)      |
| [Range](#range)       | [File](#file)       | [True / False](#true--false) | [Relationship](#relationship) | [Time Picker](#time-picker)           | [Group](#group)                       | [Choices](#field-choices)         |
| [URL](#url)           | [Gallery](#gallery) |                              | [Taxonomy](#taxonomy)         | [Color Picker](#color-picker)         | [Repeater](#repeater)                 | [Conditions](#field-conditions)   |
| [Password](#password) |                     |                              | [User](#user)                 |                                       | [Flexible Content](#flexible-content) | [Wrapper](#field-wrapper)         |
|                       |                     |                              |                               |                                       |                                       | [Location](#field-group-location) |
| [Custom / 3rd Party](#composing-custom3rd-party-addon-fields) |    |       |                               |                                       |                                       | [Position](#field-group-position) |

## Field Types

###Init
```acfstart``` for
```php
new FieldsBuilder('fields_builder', [
	'title' => 'Fields Builder',
]);
```

```acfsetlocation``` for
```php
->setLocation('post_type', '==', 'page');
```

### Basic

#### Text
```acftext``` for
```php
->addText('text_field', [ 
    'label' => 'Text field' 
])
```

```acftextx``` for
```php
->addText('text_field', [
    'label' => 'Text Field',
    'instructions' => '',
    'required' => 0,
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'default_value' => '',
    'placeholder' => '',
    'prepend' => '',
    'append' => '',
    'maxlength' => '',
])
```
[Official Documentation]( https://www.advancedcustomfields.com/resources/text)

#### Textarea
```acftextarea``` for
```php
->addTextarea('textarea_field', [ 
    'label' => 'Textarea field' 
])
```

```acftextareax``` for
```php
->addTextarea('textarea_field', [
  'label' => 'Textarea Field',
  'instructions' => '',
  'required' => 0,
  'wrapper' => [
      'width' => '',
      'class' => '',
      'id' => '',
  ],
  'default_value' => '',
  'placeholder' => '',
  'maxlength' => '',
  'rows' => '',
  'new_lines' => '', // Possible values are 'wpautop', 'br', or ''.
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/textarea)

#### Number
```acfnumber``` for
```php
->addNumber('number_field', [ 
    'label' => 'Number field' 
])
```

```acfnumberx``` for
```php
->addNumber('number_Field', [
    'label' => 'Number Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'default_value' => '',
    'placeholder' => '',
    'prepend' => '',
    'append' => '',
    'min' => '',
    'max' => '',
    'step' => '',
])
```

#### Range
```acfrange``` for
```php
->addRange('range_field', [ 
    'label' => 'Range field' 
])
```

```acfrangex``` for
```php
->addRange('range_field', [
    'label' => 'Range Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
      'width' => '',
      'class' => '',
      'id' => '',
    ],
    'default_value' => '',
    'min' => '',
    'max' => '',
    'step' => '',
    'prepend' => '',
    'append' => '',
])
```

#### Email
```acfemail``` for
```php
->addEmail('email_field', [ 
    'label' => 'Email field' 
])
```

```acfemailx``` for
```php
->addEmail('email_field', [
    'label' => 'Email Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'default_value' => '',
    'placeholder' => '',
    'prepend' => '',
    'append' => '',
])
```

#### URL
```acfurl``` for
```php
->addUrl('url_field', [ 
    'label' => 'URL Field'
])
```

```acfurlx``` for
```php
->addUrl('url_field', [
    'label' => 'URL Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'default_value' => '',
    'placeholder' => '',
])
```

#### Password
```acfpassword``` for
```php
->addPassword('password_field', [ 
    'label' => 'Password Field' 
])
```

```acfpasswordx```
```php
->addPassword('password_field', [
    'label' => 'Password Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'placeholder' => '',
    'prepend' => '',
    'append' => '',
])
```

### Content

#### Wysiwyg
```acfwysiwyg``` for
```php
->addWysiwyg('wysiwyg_field', [ 
    'label' => 'WYSIWYG Field' 
])
```

```acfwysiwygx``` for
```php
->addWysiwyg('wysiwyg_field', [
    'label' => 'WYSIWYG Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'default_value' => '',
    'tabs' => 'all',
    'toolbar' => 'full',
    'media_upload' => 1,
    'delay' => 0,
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/wysiwyg)

#### Oembed
```acfoembed``` for
```php
->addOembed('oembed_field', [ 
    'label' => 'Oembed Field' 
])
```

```acfoembedx``` for
```php
->addOembed('oembed_field', [
    'label' => 'Oembed Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'width' => '',
    'height' => '',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/oembed)

#### Image
```acfimage``` for
```php
->addImage('image_field', [ 
    'label' => 'Image field',
    'return_format' => 'array'
])
```

```acfimagex``` for
```php
$builder
    ->addImage('image_field', [
        'label' => 'Image FIeld',
        'instructions' => '',
        'required' => 0,
        'conditional_logic' => [],
        'wrapper' => [
            'width' => '',
            'class' => '',
            'id' => '',
        ],
        'return_format' => 'array',
        'preview_size' => 'thumbnail',
        'library' => 'all',
        'min_width' => '',
        'min_height' => '',
        'min_size' => '',
        'max_width' => '',
        'max_height' => '',
        'max_size' => '',
        'mime_types' => '',
    ]);
```
[Official Documentation](https://www.advancedcustomfields.com/resources/image)

#### File
```acffile``` for
```php
->addFile('file_field', [ 
    'label' => 'File field',
    'return_format' => 'array'
])
```

```acffilex``` for
```php
->addFile('file_Field', [
    'label' => 'File Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'return_format' => 'array',
    'library' => 'all',
    'min_size' => '',
    'max_size' => '',
    'mime_types' => '',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/file)

#### Gallery
```acfgallery``` for
```php
->addGallery('gallery_field', [ 
    'label' => 'Gallery field',
    'return_format' => 'array'
])
```

```acfgalleryx``` for
```php
->addGallery('gallery_field', [
    'label' => 'Gallery Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'return_format' => 'array',
    'min' => '',
    'max' => '',
    'insert' => 'append',
    'library' => 'all',
    'min_width' => '',
    'min_height' => '',
    'min_size' => '',
    'max_width' => '',
    'max_height' => '',
    'max_size' => '',
    'mime_types' => '',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/gallery)

### Choice

#### Select
```acfselect``` for
```php
->addSelect('select_field', [
    'label' => 'Select Field',
    'choices' => [
        
    ],
])
```

```acfselectx``` for
```php
->addSelect('select_field', [
    'label' => 'Select Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'choices' => [],
    'default_value' => [],
    'allow_null' => 0,
    'multiple' => 0,
    'ui' => 0,
    'ajax' => 0,
    'return_format' => 'value',
    'placeholder' => '',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/select)

#### Checkbox
```acfcheckbox``` for
```php
->addCheckbox('checkbox_field', [
    'label' => 'Checkbox Field',
    'choices' => [
        
    ],
])
```

```acfcheckboxx``` for
```php
->addCheckbox('checkbox_field', [
    'label' => 'Checkbox Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'choices' => [],
    'allow_custom' => 0,
    'save_custom' => 0,
    'default_value' => [],
    'layout' => 'vertical',
    'toggle' => 0,
    'return_format' => 'value',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/checkbox)

#### Radio
```acfradio``` for
```php
->addRadio('radio_field', [
    'label' => 'Radio Field',
    'choices' => [
        
    ],
])
```

```acfradiox``` for
```php
->addRadio('radio_field', [
    'label' => 'Radio Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'choices' => [],
    'allow_null' => 0,
    'other_choice' => 0,
    'save_other_choice' => 0,
    'default_value' => '',
    'layout' => 'vertical',
    'return_format' => 'value',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/radio-button)

#### Button Group
```acfbuttongroup``` for
```php
->addButtonGroup('button_group_field', [
    'label' => 'Button Group Field',
    'choices' => [
        
    ],
])
```

```acfbuttongroupx``` for
```php
->addButtonGroup('button_group_field', [
    'label' => 'Button Group Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
      'width' => '',
      'class' => '',
      'id' => '',
    ],
    'choices' => [],
    'allow_null' => 0,
    'default_value' => '',
    'layout' => 'horizontal',
    'return_format' => 'value',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/button-group/)

#### True / False
```acftruefalse``` for
```php
->addTrueFalse('truefalse_field', [
    'label' => 'True / False Field',
])
```

```acftruefalsex``` for
```php
->addTrueFalse('truefalse_field', [
    'label' => 'True / False Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'message' => '',
    'default_value' => 0,
    'ui' => 0,
    'ui_on_text' => '',
    'ui_off_text' => '',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/true-false)

### Relational

#### Link
```acflink``` for
```php
->addLink('link_field', [ 
    'label' => 'Link field',
    'return_format' => 'array'
])
```

```acflinkx``` for
```php
->addLink('link_field', [
    'label' => 'Link Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'return_format' => 'array',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/link)

#### Post Object
```acfpostobject``` for
```php
->addPostObject('post_object_field', [ 
    'label' => 'Post Object Field',
    'post_type' => [
        
    ],
    'taxonomy' => [
        
    ],
    'return_format' => 'object'
])
```

```postobjectx``` for
```php
->addPostObject('post_object_field', [
    'label' => 'Post Object Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'post_type' => [],
    'taxonomy' => [],
    'allow_null' => 0,
    'multiple' => 0,
    'return_format' => 'object',
    'ui' => 1,
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/post-object/)

#### Page Link
```acfpagelink``` for
```php
->addPageLink('page_link_field', [ 
    'label' => 'Page Link Field',
    'post_type' => [
        
    ],
    'taxonomy' => [
        
    ],
])
```

```acfpagelinkx``` for
```php
->addPageLink('page_link_field', [
    'label' => 'Page Link Field',
    'type' => 'page_link',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'post_type' => [],
    'taxonomy' => [],
    'allow_null' => 0,
    'allow_archives' => 1,
    'multiple' => 0,
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/page-link)

#### Relationship
```acfrelationship``` for
```php
->addRelationship('relationship_field', [ 
    'label' => 'Relationship Field',
    'post_type' => [
        
    ],
    'taxonomy' => [
        
    ],
    'return_format' => 'object'
])
```

```acfrelationshipx``` for
```php
->addRelationship('relationship_field', [
    'label' => 'Relationship Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'post_type' => [],
    'taxonomy' => [],
    'filters' => [
        0 => 'search',
        1 => 'post_type',
        2 => 'taxonomy',
    ],
    'elements' => '',
    'min' => '',
    'max' => '',
    'return_format' => 'object',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/relationship)

#### Taxonomy
```acftaxonomy``` for
```php
->addTaxonomy('taxonomy_field', [ 
    'label' => 'Taxonomy Field',
    'taxonomy' => '$ACF_TAXONOMY$',
    'field_type' => 'checkbox',
    'return_format' => 'id'
])
```

```acftaxonomyx``` for
```php
->addTaxonomy('taxonomy_field', [
    'label' => 'Taxonomy Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'taxonomy' => 'category',
    'field_type' => 'checkbox',
    'allow_null' => 0,
    'add_term' => 1,
    'save_terms' => 0,
    'load_terms' => 0,
    'return_format' => 'id',
    'multiple' => 0,
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/taxonomy)

#### User
```acfuser``` for
```php
->addUser('user_field', [ 
    'label' => 'User Field',
])
```

```acfuserx``` for
```php
->addUser('user_field', [
    'label' => 'User Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'role' => '',
    'allow_null' => 0,
    'multiple' => 0,
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/user/)

### jQuery

#### Google Map
```acfgooglemap``` for
```php
->addGoogleMap('google_map_field', [ 
    'label' => 'Google Map Field',
    'center_lat' => '',
    'center_lng' => '',
    'zoom' => '',
])
```

```acfgooglemapx``` for
```php
->addGoogleMap('google_map_field', [
    'label' => 'Google Map Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'center_lat' => '',
    'center_lng' => '',
    'zoom' => '',
    'height' => '',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/google-map)

#### Date Picker
```acfdatepicker``` for
```php
->addDatePicker('date_picker_field', [
    'label' => 'Date Picker Field',
    'display_format' => 'd/m/Y',
    'return_format' => 'd/m/Y',
    'first_day' => 1,
])
```

```acfdatepickerx``` for
```php
->addDatePicker('date_picker_field', [
    'label' => 'Date Picker Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'display_format' => 'd/m/Y',
    'return_format' => 'd/m/Y',
    'first_day' => 1,
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/date-picker)

#### Date Time Picker
```acfdatetimepicker``` for
```php
->addDateTimePicker('date_time_picker_field', [
    'label' => 'Date Time Picker Field',
])
```

```acfdatetimepickerx``` for
```php
->addDateTimePicker('date_time_picker_field', [
    'label' => 'Date Time Picker Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/date-time-picker)

#### Time Picker
```acftimepicker``` for
```php
->addTimePicker('time_picker_field', [
    'label' => 'Time Picker Field',
    'display_format' => 'g:i a',
    'return_format' => 'g:i a',
])
```

```acftimepickerx``` for
```php
->addTimePicker('time_picker_field', [
    'label' => 'Time Picker Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'display_format' => 'g:i a',
    'return_format' => 'g:i a',
    'default_value' => '',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/time-picker)

#### Color Picker
```acfcolorpicker``` for
```php
->addColorPicker('color_picker_field', [
    'label' => 'Color Picker Field',
])
```

```acfcolorpickerx``` for
```php
->addColorPicker('color_picker_field', [
    'label' => 'Color Picker Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'default_value' => '',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/color-picker/)

### Layout

#### Message
```acfmessage``` for
```php
->addMessage('message_field', [
    'label' => 'Message Field',
    'message' => '',
])
```

```acfmessagex``` for
```php
->addMessage('message_field', [
    'label' => 'Message Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
        'width' => '',
        'class' => '',
        'id' => '',
    ],
    'message' => '',
    'new_lines' => 'wpautop',
    'esc_html' => 0,
])
```

#### Accordion
```acfaccordion``` for
```php
->addAccordion('accordion_field', [
    'label' => 'Accordion Field',
    'open' => 0,
    'multi_expand' => 0,
    'endpoint' => 0,
])
->addAccordion('accordion_field_end')->endpoint();
```

```acfaccordionx``` for
```php
->addAccordion('accordion_field', [
    'label' => 'Accordion Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
      'width' => '',
      'class' => '',
      'id' => '',
    ],
    'open' => 0,
    'multi_expand' => 0,
    'endpoint' => 0,
])
->addAccordion('accordion_field_end')->endpoint();
```
[Official Documentation](https://www.advancedcustomfields.com/resources/accordion/)

#### Tab
```acftab``` for
```php
->addTab('tab_field', [
    'label' => 'Tab Field'
])
```

```acftabx``` for
```php
->addTab('tab_field', [
    'label' => 'Tab Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
      'width' => '',
      'class' => '',
      'id' => '',
    ],
    'default_value' => '',
    'placeholder' => '',
    'prepend' => '',
    'append' => '',
    'maxlength' => '',
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/tab/)

#### Group
```acfgroup``` for
```php
->addGroup('group_field', [
    'label' => 'Group Field',
    'layout' => 'block',
])

->endGroup()
```

```acfgroupx``` for
```php
->addGroup('group_field', [
    'label' => 'Group Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
      'width' => '',
      'class' => '',
      'id' => '',
    ],
    'layout' => 'block',
])

->endGroup()
```
[Official Documentation](https://www.advancedcustomfields.com/resources/group/)

#### Repeater
```acfrepeater``` for
```php
->addRepeater('repeater_field', [
    'label' => 'Repeater Field',
    'min' => 0,
    'max' => 0,
    'layout' => 'table',
])
    
->endRepeater()
```

```acfrepeaterx``` for
```php
->addRepeater('repeater_field', [
    'label' => 'Repeater Field',
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
      'width' => '',
      'class' => '',
      'id' => '',
    ],
    'collapsed' => '',
    'min' => 0,
    'max' => 0,
    'layout' => 'table',
    'button_label' => '',
])

->endRepeater()
```
[Official Documentation](https://www.advancedcustomfields.com/resources/repeater/)

#### Flexible Content
```acfflexiblecontent``` for
```php
->addFlexibleContent('flexible_content_field', [
    'min' => '$ACF_MIN$',
    'max' => '$ACF_MAX$',
])
```

```acfflexiblecontentx``` for
```php
->addFlexibleContent('flexible_content_field', [
    'instructions' => '',
    'required' => 0,
    'conditional_logic' => [],
    'wrapper' => [
      'width' => '',
      'class' => '',
      'id' => '',
    ],
    'button_label' => 'Add Row',
    'min' => '',
    'max' => '',
])
```

```acflayout``` for
```php
->addLayout('layout_field', [
    'label' => 'Layout Field',
    'sub_fields' => [
        
    ],
])
```

```acflayoutx``` for
```php
->addLayout('layout_field', [
    'label' => 'Layout Field',
    'display' => 'block',
    'min' => '',
    'max' => '',
    'sub_fields' => [
       
    ],
])
```
[Official Documentation](https://www.advancedcustomfields.com/resources/flexible-content/)

## Configuration

### Composing Fields
```php
$builder
    ->addFields(new FieldsBuilder());

$builder
    ->addField('text', 'title')
        ->setKey('field_title')
        ->setLabel('My Label')
        ->setDefaultValue('Lorem ipsum')
        ->setInstructions('This is a title.')
        ->setRequired()
            ->setUnrequired()
        ->setConfig('placeholder' => 'Enter the title');
  ```

### Composing Custom/3rd Party Addon Fields

Add any other registered custom/[3rd party ACF Fields](https://www.advancedcustomfields.com/add-ons/) using the `addField($name, $type, $args)` method.

```php
$builder
    ->addFields(new FieldsBuilder());

$builder
    ->addField('icon', 'font-awesome')
        ->setLabel('My Icon')
        ->setInstructions('Select an icon')
        ->setConfig('save_format' => 'class')

### Modifying Fields
```php
$builder
    ->modifyField('title', ['label' => 'Modified Title']);

$builder
    ->addFields(new FieldsBuilder())
        ->getField('title')
            ->modifyField('title', ['label' => 'Modified Title']);
```

### Removing Fields
```php
$builder
    ->removeField('title');
```

### Field Choices
```php
$builder
    ->addChoice('red')
    ->addChoice('blue')
    ->addChoice('green');

$builder
    ->addChoices(['red' => 'Red'], ['blue' => 'Blue'], ['green' => 'Green']);
```

### Field Conditions
```php
$builder
    ->conditional('true_false', '==', '0')
        ->and('true_false', '!=', '1')
        ->or('false_true', '==', '1');
```

### Field Wrapper
```php
$builder
    ->setWidth('30');

$builder
    ->setSelector('.field')
    ->setSelector('#field');

$builder
    ->setAttr('width', '30')
    ->setAttr('class', 'field')
    ->setAttr('id', 'field');

$builder
    ->setWrapper(['width' => '30', 'class' => 'field', 'id' => 'field']);
```

### Field Group Location

```php
$builder
    ->setLocation('post_type', '==', 'page')
        ->and('page_type', '==', 'front_page');
```

#### Field Group Locations

* **Post**: `post_type`, `post_type_list`, `post_type_archive`, `post_template`, `post_status`, `post_format`, `post_category`, `post_taxonomy`, `post`
* **Page**: `page_template`, `page_type`, `page_parent`, `page`
* **User**: `current_user`, `current_user_role`, `user_form`, `user_role`
* **Forms**: `taxonomy`, `taxonomy_list`, `attachment`, `comment`, `widget`, `nav_menu`, `nav_menu_item`, `block`, `options_page`
* **Custom**: [Official Documentation](https://www.advancedcustomfields.com/resources/custom-location-rules/)

### Field Group Position
```php
$builder = new FieldsBuilder('banner', ['position' => 'side']); // acf_after_title, normal, side
```
