---
title: 'Row element (dsQueryResponse)'
description: Represents a row of data from the list.
manager: soliver
ms.date: 12/14/2020
ms.audience: Developer
ms.topic: reference
ms.prod: sharepoint
ms.localizationpriority: medium
api_name:
  - dsQueryResponse XML
ms.assetid: e2d1bbbe-c920-41d0-994a-f06a122ba3fd
---

# Row element (dsQueryResponse)

**Applies to:** SharePoint 2016 | SharePoint Foundation 2013 | SharePoint Online | SharePoint Server 2013

Represents a row of data from the list. The fields and metadata properties of the list item that the row contains are represented by attributes of the **Row** element. Some fields, depending on their data type, may be represented by additional attributes that present the field's value in a different format.

```XML
<Row
  Attachments="Integer"
  ContentTypeId="GUID"
  File_x0020_Type="String"
  FileLeafRef="String"
  FileLeafRef.Name="String"
  FileLeafRef.Suffix="String"
  FSObjType="Integer"
  HTML_x0020_File_x0020_Type.File_x0020_Type.mapall="String"
  HTML_x0020_File_x0020_Type.File_x0020_Type.mapcon="String"
  HTML_x0020_File_x0020_Type.File_x0020_Type.mapico="String"
  ID="Integer"
  PermMask="Hex"
  some_field="type appropriate to the field"
  some_booleanField.Value="Integer"
  some_date_time_field.ifnew="Integer"
  some_date_time_field.="unlocalized DateTime"
  some_date_time_field.DateOnly="date"
  some_date_time_field.TimeOnly="time"
  some_date_time_field.ISO8601="ISO8601 compliant DateTime"
  some_date_time_field.MonthDayOnly="month and day"
  some_date_time_field.MonthYearOnly="month and year"
  some_user_field="String"
  some_user_field.id="Integer"
  some_user_field.title="String"
  some_user_field.span="String"
  some_url_field.desc="String"
/>
```

## Elements and attributes

The following sections describe attributes, child elements, and parent elements.

### Attributes

| Attribute                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| :---------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Attachments**                                       | Required. **1** if the list item has one or more attachments; otherwise, **0**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **ContentTypeId**                                     | Required. The GUID of the content type of the list item in the format Ox _GUID_without_hyphens_.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| **File_x0020_Type**                                   | Required, but ignored if the list is not a document library. The type of files in a document library. Empty string when the list is not a document library.                                                                                                                                                                                                                                                                                                                                                                                          |
| **FileLeafRef**                                       | Required, but ignored if the list is not a document library. The server-relative URL of the document. This is the folder name, followed by `"_."`, followed by the file name. An example is `QuarterlySummaries_.Quarter1.docx`. This attribute value is the concatenation of the values of the **FileLeafRef.Name** attribute and the **FileLeafRef.Suffix** attribute with a `"."` separator character.                                                                                                                                            |
| **FileLeafRef.Name**                                  | Required, but ignored if the list is not a document library. The name of the folder that contains the document, followed by an underscore character; for example, `QuarterlySummaries_.`                                                                                                                                                                                                                                                                                                                                                             |
| **FileLeafRef.Suffix**                                | Required, but ignored if the list is not a document library. The name of the document file; for example, `Quarter1.docx`.                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **FSObjType**                                         | Required. **1** if the list item is a folder; otherwise, **0**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **HTML_x0020_File_x0020_Type.File_x0020_Type.mapall** | Optional. The value that is returned by a call of the **MapToAll** function during the XSLT transformation. For more information, see [MapToAll Element (View)](maptoall-element-view.md) and [SharePoint Data View web part Extension Functions in the ddwrt Namespace](https://msdn.microsoft.com/library/dd583143%28office.11%29.aspx).                                                                                                                                                                                                           |
| **HTML_x0020_File_x0020_Type.File_x0020_Type.mapcon** | Optional. The value that is returned by a call of the **MapToControl** function during the XSLT transformation. For more information, see [MapToControl(SPWeb, String, String)](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPUtility.MapToControl.aspx), [MapToControl element (View)](maptocontrol-element-view.md), and [SharePoint Data View web part Extension Functions in the ddwrt Namespace](https://msdn.microsoft.com/library/dd583143%28office.11%29.aspx).                                                        |
| **HTML_x0020_File_x0020_Type.File_x0020_Type.mapico** | Optional. The value that is returned by a call of the **MapToIcon** function during the XSLT transformation. For more information, see [Icon()](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPUtility.Icon.aspx), [MapToIcon Element (View)](maptoicon-element-view.md), and [SharePoint Data View web part Extension Functions in the ddwrt Namespace](https://msdn.microsoft.com/library/dd583143%28office.11%29.aspx).                                                                                                      |
| **ID**                                                | Required. The ID of the list item.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **PermMask**                                          | The permissions mask for the list item.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| _some_field_                                          | Required for every non-hidden field in the list item. For each such field, there is an attribute that has the same name as the internal name of the field.                                                                                                                                                                                                                                                                                                                                                                                           |
| _some_field_                                          | Optional. The currency, number, and lookup field types in SharePoint Foundation may have a low-level formatting even before any HTML formatting is applied. For example, a negative currency value is enclosed in parentheses. The attribute of each such field is immediately followed by another attribute that has the same name, to which a `"."` character is appended. This attribute provides the field value as raw unformatted data. For example, a negative currency value is proceeded by a minus sign (`"-"`) and is not in parentheses. |
| _some_booleanField_ **.Value**                        | Optional. Every **Boolean** attribute in the list item is followed by another attribute that has the same name, to which `".Value"` is appended. This attribute gives the raw unlocalized form of the field value (1 or 0), whereas the main attribute for the **Boolean** field gives the value relativized to the website's locale.                                                                                                                                                                                                                |
| _some_date_time_field_ **.ifnew**                     | Optional. **1** if the date time value is recent enough to define the list item as new; otherwise, **0**. This attribute appears only if the _some_date_time_field_ is "Created_x0020_Date".                                                                                                                                                                                                                                                                                                                                                         |
| _some_date_time_field_                                | Optional. If there is an attribute for a datetime field whose value is localized, there is also an attribute that has the same name, to which a `"."` character is appended. This attribute provides the raw value of a datetime field as stored in the content database in ISO8601 format.                                                                                                                                                                                                                                                          |
| _some_date_time_field_ **.DateOnly**                  | Optional. The value of a DateTime field with only the date. Used only on blog-related lists.                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| _some_date_time_field_ **.TimeOnly**                  | Optional. The value of a DateTime field with only the time of day. Used only on blog-related lists.                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| _some_date_time_field_ **.ISO8601**                   | Optional. The value of a DateTime field formatted in compliance with ISO8601. Used only on blog-related lists.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| _some_date_time_field_ **.MonthDayOnly**              | Optional. The value of a DateTime field with only the month and day of month. Used only on blog-related lists.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| _some_date_time_field_ **.MonthYearOnly**             | Optional. The value of a DateTime field with only the month and year. Used only on blog-related lists.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| _some_user_field_ **.id**                             | Optional. If any attribute represents a User type field, there is another attribute that has the same name, to which `".id"` is appended. This is the site-relative ID number of the user.                                                                                                                                                                                                                                                                                                                                                           |
| _some_user_field_ **.title**                          | Optional. If any attribute represents a User type field, there is another attribute that has the same name, to which `".title"` is appended. This is the name of the user, for example "Michiyo Sato". Note that the value of the main attribute, _some_user_field_, is the HTML **span** markup for the user, including, for example, presence information. See the code excerpt below the table for an example.                                                                                                                                    |
| _some_user_field_ **.span**                           | Optional. If any attribute represents a User type field, there is another attribute that has the same name, to which `".span"`is appended. This is a plainer version of the HTML markup for the user. See the code excerpt below the table for an example.                                                                                                                                                                                                                                                                                           |
| _some_url_field_ **.desc**                            | Optional. If any attribute represents a URL field, there is another attribute that has the same name, to which ".desc" is appended. This provides a description of the URL.                                                                                                                                                                                                                                                                                                                                                                          |

This markup is used to render the field when the [FreeForm](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewFlags.FreeForm.aspx) flag of the [ListViewWebPart.ViewFlags](https://msdn.microsoft.com/library/Microsoft.SharePoint.WebPartPages.ListViewWebPart.ViewFlags.aspx) property is not set; otherwise the value of the _some_user_field_ **.span** attribute is used.

```xml
<span class="ms-imnSpan">
  <a href='javascript:;' onclick='IMNImageOnClick(event);return false;' class='ms-imnlink'>
    <img name='imnmark' class='ms-imnImg' title='' border='0' height='12' width='12'
         src='/_layouts/images/blank.gif'
         alt='No presence information'
         sip='MichiyoS@Contoso.com'
         id='imn_1,type=smtp' />
  </a>
  <a onclick="GoToLink(this);return false;" href="/sites/Contoso/_layouts/userdisp.aspx?ID=1">Michiyo Sato</a>
</span>
```

This markup is used to render the field when the [FreeForm](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPViewFlags.FreeForm.aspx) flag of the [ListViewWebPart.ViewFlags](https://msdn.microsoft.com/library/Microsoft.SharePoint.WebPartPages.ListViewWebPart.ViewFlags.aspx) property is set; otherwise the value of the _some_user_field_ **.title** attribute is used.

```xml
<nobr>
  <span>
    <a onclick="GoToLink(this);return false;" href="/sites/Contoso/_layouts/userdisp.aspx?ID=1">Michiyo Sato</a>
    <img border="0" height="1" width="3" src="/_layouts/images/blank.gif"/><a href='javascript:;' onclick='IMNImageOnClick(event);return false;' class='ms-imnlink'>
    <img name='imnmark' class='ms-imnImg' title='' border='0' height='12' width='12'
         src='/_layouts/images/blank.gif'
         alt='No presence information'
         sip='MichiyoS@Contoso.com' id='imn_2,type=smtp'/></a>
  </span>
</nobr>
```

### Child elements

None

### Parent elements

- [Rows](rows-dsqueryresponse.md)

### Occurrences

- Minimum: 0
- Maximum: the value of the **RowLimit** attribute of the parent **dsQueryResponse** element

## Example

For an example, see [Examples of Input and Result Node Trees in XSLT Transformations](https://msdn.microsoft.com/library/cbe88144-25ac-4cd2-8f2a-50e8c271c6ae%28Office.15%29.aspx).
