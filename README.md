# Paragraph Formatter

This module provides an additional formatter "Paragraph Id(s)" for entity_reference_revision fields.

## Common use-case of this module:

you would like to create a view in "Serializer" format to output entities and its referenced paragraphs in JSON format 
for example. The default use of the views-feature "Relationships" causes potentially several rows for an entity: a row 
by paragraph/entity-reference value. By the use of this little helper-module you can use a sub-view in your main-view 
that outputs the paragraph fields of your choice.
### Quick-and-dirty HowTo:
* Install the module "Views Field View" which let's you integrate a sub-view in your main view. 
https://www.drupal.org/project/views_field_view
* Install this module "Paragraph Formatter".
* Create a view to output the paragraph-fields of your choice, we name it for our example "paragraphs"
    * Format: Serializer
    * Show fields
    * Contextual filters: Paragraph:ID ... and check under "MORE" Allow multiple values !
* Create another view to output your content-entities which contain on other paragraphs.
    * Format: Serializer
    * Show fields
    * Add fields of your choice
    * Add your entity_reference_revision field refrencing the paragraphs.
        * check exclude from display
        * select "Paragraph Id(s)" as Formatter
        * under "Multiple Field Settings" check
            * Display all values in the same row
            * Simple separator
            * Separator: ","
    * Add a field Global: View
        * Select under "View settings" our earlier created sub-view "Paragraphs" with display "Rest-export" 
        * insert under "Contextual filters" the token for our earlier added entity_reference_revision field, 
        see "Replacement Patterns". 

Thats it.    
