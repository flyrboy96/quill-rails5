# Quill::Rails5

This gem provides simple way to use Quill.js Rich Text Editor in Rails applications.

The gem helpers load Quill.js from the CDN, render and initialise Quill editor and optionally link rich text editor with form using Rails FormBuilder.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'quill-rails5', github: 'flyrboy96/quill-rails5'
```

## Usage

The simplest way to load editor is to call

```erb
<%= quill({}, {}) %>
```

For more advanced use, the gem allows to specify html options and default value
```erb
<%= quill({}, style: 'height:35em') do %>
  <%= santize default_contents %>
<% end %>
```

## Usage with forms

To use Quill editor inside a FormBuilder form, the gem provides `quill_field` helper:
```erb
<%= quill_field f, :name, :field_id, 'editor_name' %>
```
where `f` is a FormBuilder instance (from `form_for do |f|`), `:name` is name of the field in form object, and `:field_id` is the id of the field to use.

This helper renders a hidden field and uses jQuery to update hidden field on form submission.

## To support multiple editor configurations

In order to have two different editors:

Declare the editors with their custom names
```erb
<%= quill({}, {editor: 'editor-1'}) %>
<%= quill({}, {editor: 'editor-2'}) %>
```

Create a `quill_field` for each hidden field, setting their editor tags to accept changes from the specified editor.
```erb
<%= quill_field f, "content[body]", :widget_content_body, 'editor-1' %>
<%= quill_field f, "content[body]", :widget_content_body, 'editor-2' %>
```

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

