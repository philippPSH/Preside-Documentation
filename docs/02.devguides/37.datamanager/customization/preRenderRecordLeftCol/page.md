---
id: datamanager-customization-prerenderrecordleftcol
title: "Data Manager customization: preRenderRecordLeftCol"
---

## Data Manager customization: preRenderRecordLeftCol

The `preRenderRecordLeftCol` customization allows you to add custom HTML _above_ the left-hand column of the core view record screen for your object (see [[adminrecordviews]]). The action is expected to return a string containing the HTML and is provided the following in the `args` struct:

* `objectName`: The object name
* `recordId`: ID of the record
* `version`: Version number of the record (if the object is versioned)

>>>>>> You can also make use of variables in the `prc` scope, such as `prc.record`, that will allow you to potentially not duplicate calls to the database.

For example:

```luceescript
// /application/handlers/admin/datamanager/blog.cfc

component {

	private string function preRenderRecordLeftCol() {
		args.blog = prc.record ?: QueryNew('');

		return renderView( view="/admin/blogs/auditTrail", args=args );
	}

}
```
