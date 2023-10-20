# MS Access unexpected truncation

MS Access - demo of unexpected truncation when selecting a query result into a new table.

## How to reproduce

* Note tbl1 has one Long Text field called blog_post.
* qry1 runs this field through a VBA function. 
* The definition of Query select_qry1_into_new_tbl is `SELECT * INTO tbl_made_from_qry1 FROM qry1`
* Run this query and note that the blog_post value has been truncated to fit into a Short Text field.
