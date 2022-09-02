# Design approach

When considering design approach we want to ensure each of our apps have a consistent look and feel but also considering the time and effort often put into designing components. As a result, we follow this approach.

## Reusable Components

Where we identify a need for reusable components we will create [components](https://docs.microsoft.com/en-us/power-apps/maker/canvas-apps/create-component) in the scope of the application (for app specific designs) or as an addition to our [component library](https://docs.microsoft.com/en-us/power-apps/maker/canvas-apps/component-library) (where we would want to reuse a component accross our entire estate). Components we design will follow the principles set out in the [ONS Design System](https://ons-design-system.netlify.app/) or the [GOV.UK Design System](https://design-system.service.gov.uk/).

We also have reusable theme which can either be included with the component library or a lighter version as a collection within the App.OnStart. The colour palettes used are those found on the [ONS Design System](https://ons-design-system.netlify.app/).

## Out-of-the-box

Microsoft has done significant work on their [Modern Fluent UI](https://powerapps.microsoft.com/en-us/blog/modern-fluent-ui-controls-in-power-apps-preview/) to make them easy to use and accessible. So where possible, significant redesign or restyling should not be undertaken on individual base components. This could include:

1. Labels
2. Inputs
3. Text areas

If there is a need to change the design or style of the OOTB components, consideration should be given to creating a component and adding them to the reusable component library.
