# Introduction

Completed100 XP

-   7 minutes

Microsoft Power BI provides numerous design tools to help you with report layout. Knowing about these tools and how to use them will help you reduce report creation time and produce more visually appealing results.

The report design tools include:

-   Format commands
    
-   **Selection** pane
    
-   Report layout options
    
-   Page view
    
-   Undo/redo
    

## Format commands

The **Format** contextual ribbon tab, which is available when you select one or more report objects, contains several commands to help you arrange objects on the page.

[![Screenshot of the Format tab on Power BI Desktop.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/format-contextual-ribbon.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/format-contextual-ribbon.png#lightbox)

You can use this tab to manage the layer order for one or more objects, with options to move objects forward or backward or directly to the upper or lower layer. You might deliberately overlap visuals when switching visibility state with bookmarks or when superimposing objects, like text boxes or visuals, on background shapes.

Various options are available to help you align objects horizontally or vertically. Well-aligned objects result in a balanced and visually appealing page layout. When you select a single object, you can align it with the report page. When selecting multiple objects, you can align them among one another. You can also distribute multiple selections of objects horizontally or vertically, ensuring that equal spacing separates the objects. The distribution options require that at least three objects are selected.

Grouping options let you treat the group like a single object, making the process of moving, resizing, and working with layers in your report simpler, faster, and more intuitive. Additionally, you can group, ungroup, or merge other objects into an existing group.

For more information, see [Group visuals in Power BI Desktop reports](https://learn.microsoft.com/en-us/power-bi/create-reports/desktop-grouping-visuals/).

## Selection pane

The **Selection** pane has two tabs: **Layer order** and **Tab order**.

### Layer order

The **Layer order** tab contains a list of all objects and groups of objects that are found on the page, together with the visibility state. When the name of each item in the list is set, it can have a generic label, such as **button** or **slicer**, or the object title property. Renaming an object in this pane will update the title property.

[![Screenshot of the Selection pane and the Layer order tab. Several objects and groups are listed.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/selection-pane-layer-order.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/selection-pane-layer-order.png#lightbox)

You can complete several tasks in the **Layer order** tab. You can use the tab to select a single object or group, or to select multiple objects or groups. Often, you might find it simpler and quicker to select objects by using the pane instead of selecting the objects on the page, especially for complex, multilayered layouts.

You can set the visibility state to hide or unhide individual objects or groups. Hiding objects can help unclutter a report page at design time. Advanced report layouts can use bookmarks to capture the visibility state, allowing report consumers to control visibility with buttons.

You can also modify the layer order, often referred to as _z-order_. Because you can overlap objects (or groups) on the page, the higher an object appears in the layer order, the closer it is to the front. Therefore, when you have overlapping objects, the one that is listed first is on top. To change order, drag an object or group to a new position.

### Tab order

In the **Tab order** tab, you can manage tab order.

[![Screenshot of the Selection pane and the Tab order tab. Several objects and groups are listed.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/selection-pane-tab-order.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/selection-pane-tab-order.png#lightbox)

By pressing the **Tab** key, you can configure the tab order to ensure that keyboard navigation follows a logical sequence. The **Tab order** tab also allows screen readers to read aloud the objects in a logical order. Additionally, you can remove an object from the tab order by selecting the numeric value at the left of the object.

 Note

Accessibility is described in Unit 5.

## Report layout options

On the **View** ribbon tab, you can enable gridlines, snap to grid, and lock objects. These three options apply to all report pages and aren't persisted, so you will need to re-enable them each time that you edit the report.

[![Screenshot of the View tab, showing the page options of Gridlines, Snap to grid, and Lock objects.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/view-ribbon-tab-page-options.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/view-ribbon-tab-page-options.png#lightbox)

When you enable the **Gridlines** option, visible guides appear that can help you align visuals. The gridlines can help make it easier for you to ensure that two (or more) visual borders are aligned horizontally or vertically.

You can enable the **Snap to grid** option to align visuals on the page, resulting in a more visually pleasing layout. When you move or resize visuals, the report designer will attempt to align them to the nearest gridline.

If the **Lock objects** option is enabled, you can't resize or move visuals. You might find this option helpful when you want a report reading experience and you want to avoid accidentally modifying the layout. When objects are locked, you can still modify the position and size of visuals by using the **Format** options (in the **General** section).

 Tip

Occasionally, the **Snap to grid** feature will try to align visuals in an unintended way. While moving or resizing a visual, you can temporarily override the snap-to-grid behavior by pressing the **Windows** key.

## Page view

You can scale the report canvas to fit to page, fit to width, or show actual size. Full screen mode isn't an option during report design; it's only supported for report consumers when the report is viewed in Power BI service or a Power BI mobile app. A zoom control isn't available to enlarge or reduce the report canvas.

[![Screenshot of the View tab, showing the Page view command.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/view-ribbon-tab-page-view.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/view-ribbon-tab-page-view.png#lightbox)

 Tip

Whenever possible, use the largest available monitor size and then maximize the Power BI Desktop window. To maximize the report canvas, consider closing or minimizing panes, such as the **Fields** pane. You can also collapse the ribbon to the condensed view.

## Undo/redo

Similar to many Microsoft products, you can undo or redo actions by pressing the **Ctrl+Z** or **Ctrl+Y** keyboard shortcuts, respectively. In Power BI Desktop, these options are also available in the quick access area, which is located in the upper-left corner. Try experimenting when authoring reports to find what works because it's simple to undo the last action(s) that you made.

[![Screenshot of the Undo quick access command, located in the upper-left corner of the Power BI Desktop window.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/undo.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/undo.png#lightbox)

 Tip

Many other shortcuts are available in Power BI Desktop. You can use the **Shift+?** keyboard shortcut to view a complete list of keyboard shortcuts.

# Design visually appealing reports

Completed100 XP

-   9 minutes

Having the correct data and selecting the correct visuals is important. Equally as important is ensuring that the report is visually appealing. A well-designed report should guide the report consumer to quickly find and understand the answers to their questions.

While striving to produce an appealing report, bear in mind that the report should be user-friendly. Moreover, it might be possible to add more visuals to a well-designed report page without it appearing cluttered.

## Space

Space is essential for an effective report design because it helps reduce clutter and increase readability. Spacing applies to the report page margins and the spacing between report objects.

### Margins

Margins include the border area, or edge, around each page. Having a consistently spaced border area frames the report objects.

Because there isn't a report page property to set margins, it's up to you to lay out objects in way that results in a consistent border area. Margin sizes should be equal on the left and right, with possible variation on the top and bottom. Space across the top or bottom can show branding, titles, slicers, or other information that needs to be separated from the visuals.

The following report shows the consistent spacing (highlighted with dashed lines) around the border area of the page.

[![Screenshot of a report page with margin spacing highlighted on the left, right, top, and bottom of the page.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/spacing-margins.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/spacing-margins.png#lightbox)

### Object spacing

Ensure that you provide sufficient space surrounding, or within, report objects.

 Note

When visual headers are enabled, be sure to test that they don't overlap with nearby objects because overlapping objects can make interacting with visual header icons difficult. Appropriate spacing between visuals will help you avoid this problem.

Consider using different space depth to visually separate sections of related objects.

However, keep in mind that too much space can result in an unbalanced report layout and could draw the report consumer's attention away from what matters. Moderation is key: Always strive to produce an evenly spaced and balanced report.

Spacing is described in more detail in the **Alignment** topic.

## Size

Size can relate to the page size and visual size.

### Page size

You can set the page size to predefined or custom dimensions. Additionally, you can set custom dimensions that are larger than the available screen size so that the report consumer will need to interact with scrollbars to view the entire page.

[![Screenshot of the format options, Page size section, showing Type set to Custom, with specific width and height pixel values.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/page-size.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/page-size.png#lightbox)

However, a large page size that is filled with visuals might take time to render, and visuals might not render in a top-to-bottom order.

### Visual size

Generally, the more important the visual, the larger its size. Report consumers will quickly focus on larger visuals. When similar visuals are on the page, such as a series of card visuals, they should be equally sized.

Many visuals are responsive to size, so the visual will look appealing in either a small or large size. Consider that a line chart visual might appear like a sparkline when it's sized as small. In this case, only a few axis and data labels might appear. When the line chart visual is sized larger, more detail will be revealed, including many more axis and data labels.

While report consumers can use focus mode to enlarge a single visual, the visual should still clearly communicate its data when viewed at actual size on the report page. Focus mode can help consumers better interpret the data or more easily interact with the visual, such as expanding into levels of a matrix or decomposition tree visual.

## Alignment

When multiple visuals are on the report page, ensure that they're properly aligned, meaning that the edges of visuals should be in alignment and the spacings between visuals are consistent.

Alignment also relates to format options. For example, the alignment of titles and legends _within visuals_ should be consistent.

Consider laying out the report page with different sections and aligning visuals appropriately within the sections. Sections can be _implied_ or _explicit_.

### Implied sections

Define implied sections by aligning groups of visuals in close proximity. The following example shows how spacing separates the visuals. This example demonstrates how well-applied spacing (highlighted with dashed lines) can convey association, and guide the report consumer's attention while providing balance and structure to the report page.

[![Screenshot of a report page with spacing between the seven visuals to produce an implicit section in the upper-left corner of the page.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/alignment-implied-section.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/alignment-implied-section.png#lightbox)

### Explicit sections

You can define explicit sections by using colored shapes and overlaying aligned visuals on those shapes. The following example shows how the colored background shapes and spacing (highlighted with shading) separate the visuals into three sections.

[![Screenshot of a report page with margin spacing highlighted in the left, right, top, and bottom, and with spacing and background shapes that separate the visual into three sections.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/alignment-explicit-sections.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/alignment-explicit-sections.png#lightbox)

 Tip

Use the alignment commands on the **Format** tab, which will help you quickly and accurately align visuals.

## Color

Use color sparingly and meaningfully because overusing it can be distracting. Stick to a few softer colors as a base, possibly aligned with corporate colors. Softer colors ensure that the data is the focus in your report. Reserve the use of bolder colors to highlight exceptions.

Ensure that colors are sufficiently contrasting. Color contrast is especially important to create accessible reports for report consumers who have low vision. This topic is described in more detail in Unit 5.

The following example shows several issues that are related to color. The colors that are applied on the left side of the page are different from those that are applied on the right side. Also, the colors are bright and can possibly distract the report consumer. Some colors, such as yellow, don't provide sufficient contrast with the white data labels.

[![Screenshot of a report page with the color issues that are previously described.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/color-example-bad.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/color-example-bad.png#lightbox)

In the following image, the report layout is improved with the use of better colors. The colors are now consistent and provide suitable contrast with the white data labels.

[![Screenshot of a report page with the color issues resolved.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/color-example-good.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/color-example-good.png#lightbox)

## Consistency

Strive for consistency when you are laying out and configuring report objects. Consistency should apply to everything in your report design, including spacing, margins, size, alignment, and especially to object format options. Format options include the selection of font, font size, font weight, colors, and many other styling options. Format options also include the enabling of visual features like axis labels and data labels.

The following example shows many inconsistencies, including mixed fonts, different font sizes, and inconsistent titles. At first glance, the report appears unbalanced.

[![Screenshot of a report page with the inconsistencies described in the previous section.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/consistency-example-bad.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/consistency-example-bad.png#lightbox)

The quickest way to enforce consistency is to use a _report theme_. A report theme applies format settings to your entire report, ensuring consistent application of colors, fonts, pages, and visual format options, including the **Filters** pane styles.

Consider using one of the many built-in themes from the theme gallery. You can use one as a starting point and then customize it to better meet your requirements. Alternatively, you can create a new theme, which can be considerable work initially, but will provide you with granular control.

 Note

Be aware that the theme will be overridden when you explicitly configure a format option. For example, you can explicitly set a color by entering a HEX value instead of selecting a color from the palette. Try to limit overriding the report theme to an exception basis because if you switch themes, overridden properties won't update.

Be sure to export the report theme, which is a JSON file, and then apply it to other reports to ensure consistency across all reports.

 Tip

You can use an external site like [powerbi.tips](https://powerbi.tips/) to generate a theme. The site will guide you through building a color palette and setting property values for all core visual types.

For more information, see [Use report themes in Power BI Desktop](https://learn.microsoft.com/en-us/power-bi/create-reports/desktop-report-themes/).

# Case study - Create a visually appealing report

Completed100 XP

-   1 minute

In this unit, you will explore how a sales report design for the Contoso Skateboard Company evolves from a basic layout to a visually appealing report.

In the following report, read the accompanying text and then select the icons along the lower-left corner to work through the seven steps. These steps will allow you to observe the transformation of a basic layout into a visually appealing report. After working through the seven steps, select the final icon to review the before/after views to fully appreciate the final result.

[![Screenshot of the seven icons that are located in the lower-left corner of the report page. Use the Tab key to navigate to the icons in the report. A screen reader can read aloud a description for each icon.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/case-study-seven-steps.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/case-study-seven-steps.png#lightbox)

 Tip

You can maximize the report by selecting the double-headed arrow in the lower-right corner. When you're ready to return to the module, press the **Esc** key.

# Reformat reports for mobile consumption

Completed100 XP

-   2 minutes

Power BI offers a set of mobile apps for iOS and Android mobile devices. The app allows consumers to connect to and interact with Power BI reports.

While report consumers can view any Power BI report page in landscape orientation, you can provide an improved consumption experience in portrait orientation. You can complete this action by creating a mobile view for each report page that's designed for mobile devices when opened in portrait view.

You can add any page visual, including slicers, to the mobile view. Furthermore, visuals are responsive, meaning that they change dynamically to display the maximum amount of data, regardless of size.

[![Screenshot of a report in a tablet device beside the same report that is laid out vertically in a mobile phone.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/mobile-layout.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/mobile-layout.png#lightbox)

In the Power BI mobile app, report consumers can identify a mobile-optimized report by a special icon. The following example shows that the Power BI mobile app lists two reports, each accompanied by a different icon. The first report is **Retail Analysis**, which isn't optimized for mobile view. The second report is **Sales & Returns**, which is a mobile-optimized report.

[![Screenshot of two report icons. The first is for a non-optimized report and the second is for a mobile-optimized report. The second icon includes a mobile phone icon.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/mobile-icon.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/mobile-icon.png#lightbox)

When report consumers open a mobile-optimized report, the report opens in mobile-optimized mode. If they hold their device in landscape orientation, the report opens in unoptimized mode.

For more information, see [Optimize Power BI reports for the mobile app](https://learn.microsoft.com/en-us/power-bi/create-reports/desktop-create-phone-report/).

# Design reports for accessibility

Completed100 XP

-   5 minutes

Currently, over 1 billion people in the world live with a disability. Accessibility is about ensuring that all people, regardless of ability, have equal access to physical and electronic environments and resources.

Some people with disabilities use assistive technology such as screen readers, screen magnifiers, and speech recognition tools. Microsoft ensures that its products, apps, and services offer exceptional experiences to people who are using assistive technology.

Power BI supports certain accessibility features that you can factor into your report designs. The product allows you to create reports that are usable by the widest possible audience without the need for them to adapt for special accessibility requirements. Therefore, you should always design with accessibility in mind and avoid creating a new report version that addresses a particular accessibility requirement. Make sure that you consider report consumers who have visual impairments or who rely on keyboard or voice-activated interaction.

You can meet accessible report designs by using suitable format options or by applying built-in accessibility features.

## Styling

To help report consumers who have low vision, use non-serif fonts and lean toward larger font sizes. To support report consumers with color blindness, use high contrast colors. Consider using a built-in theme, like _Color blind safe_ or _High contrast_.

 Note

When the high contrast option is enabled in Windows, Power BI automatically applies those settings to reports. However, in some cases, Power BI can't automatically detect this setting. In that case, the report consumer can manually apply contrast colors by using the **View** menu.

By default, data series are distinguished by different colors. You can further distinguish the data series by using line styles or markers.

In the following line chart visual, shapes help distinguish the two data series.

[![Diagram of a line chart visual with two data series. One series uses a circle marker. The second series uses a square marker.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/accessibility-styling-markers.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/accessibility-styling-markers.png#lightbox)

In the following line chart visual, line styles help distinguish the two data series.

[![Diagram of a line chart visual with two data series. One series uses a solid line. The second series uses a dotted line.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/accessibility-styling-line-style.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/accessibility-styling-line-style.png#lightbox)

## Alt text

Alternative text descriptions, or _alt text_, can describe the appearance and function of report objects to screen reader users. Every report object has an alt text property, which is set in the **General** section of the **Format** options.

[![Screenshot of the Alt Text property in the Format options.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/accessibility-alt-text.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/accessibility-alt-text.png#lightbox)

For data visuals, don't describe specific data points in alt text because data values are likely to change. However, it's possible to assign a measure, which uses Data Analysis Expressions (DAX), to the alt text property. That way, the measure could evaluate the filter context and return a text description of the data.

 Tip

To learn more about DAX, see [Use DAX in Power BI Desktop](https://learn.microsoft.com/en-us/training/paths/dax-power-bi/).

## Tab order

Ensure that the tab order (which is set in the **Selection** pane) for each page follows a logical sequence. Additionally, make sure that you remove report objects from the tab order if they're purely decorative, such as a background shape or image. A well-configured tab order allows screen readers to read aloud relevant objects in a logical order. For data visuals, screen readers always read aloud the title, visual type, and any alt text.

 Tip

To enhance the screen reader experience, keep titles concise yet friendly, and avoid using acronyms and abbreviations.

## Conditional formatting

Several conditional formatting options are available for you to use to highlight values in grid data visuals, such as the table and matrix visuals. The _icon_ option is especially useful. It helps you convey status with color and icon.

The following matrix visual shows that the **Days sales of inventory** column communicates zero on-hand stock by using an icon (exclamation mark) and color (red).

[![Screenshot of a matrix visual with conditional formatting as described in the previous section.](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/accessibility-conditional-formatting-icon.png)](https://learn.microsoft.com/en-us/training/modules/power-bi-effective-ui/media/accessibility-conditional-formatting-icon.png#lightbox)

## Report consumption experience

Report consumers should be able to fully use and interact with your reports. Be sure that you educate them on how to:

-   Apply high contrast color themes (use the **View** menu).
    
-   Use the **Tab** key to navigate between report objects on the page.
    
-   Use many different keyboard shortcuts to shift focus into visuals, navigate between data points, select one or more data points, or clear selections (use **Shift+?** for a complete list).
    
-   Use focus mode to zoom into a visual.
    
-   Show the data table to view the underlying data of a visual in tabular format (use **Alt+Shift+F11**).
    

For more information, see [Design Power BI reports for accessibility](https://learn.microsoft.com/en-us/power-bi/create-reports/desktop-accessibility-creating-reports/).

# Publish and manage reports


After you've completed the UI enhancements, you're ready to prepare your report for publication. Before you publish the report, you will need to test it. You should also understand how to successfully manage future changes.

## Testing

Make sure that you test your report prior to publication. Undergo user acceptance testing (UAT) to ensure that the report meets requirements and report consumer expectations. Be sure to collect and review feedback and implement necessary changes. If possible, observe report consumers working with the report to determine if they use it in the ways that you intended. You might be surprised by what they do and the functionality that they overlook.

Additionally, be sure to test the report by using all possible interfaces, whether it's the Power BI service, a mobile app, or an embedding app.

## Prepare for publication

Before you publish the report, ensure that the state of the report aligns with the intended initial experience. Reset filters and slicers, visual drill state, sort orders, and button state (for buttons that switch visibility of report objects). Lastly, select the first page of the report. Then, you'll be ready to save the report and publish it to Power BI.

## Provide support

Be sure to provide support for your report so that report consumers understand how to best use it. Assistance can be provided in many different ways:

-   Training, which can be informal (such as a lunch meeting) or formal (like a structured course)
    
-   Recorded demonstration
    
-   Built-in assistance with an information page, visual header tooltips, or an overlay that is made visible when report consumers select a button
    
-   Documentation
    

For more information, see [Power BI adoption roadmap: Mentoring and user enablement](https://learn.microsoft.com/en-us/power-bi/guidance/powerbi-adoption-roadmap-mentoring-and-user-enablement/).

## Manage change

Often, it's better to publish a new report that includes many updates than release smaller incremental changes. This approach makes it easier for you to inform your audiences of changes. Consider using deployment pipelines to better manage the life cycle of organizational content. For more information, see [Introduction to deployment pipelines](https://learn.microsoft.com/en-us/power-bi/create-reports/deployment-pipelines-overview/).

Avoid deleting and re-creating a report. It's better to publish and overwrite an existing report so that links and personalized settings continue to work.

Report modifications might invalidate personal bookmarks, personalized visuals, persistent filters, or other per-user data settings (drill state, sort order, and so on). Whenever possible, avoid breaking these personal enhancements because it can contribute to report consumer dissatisfaction.