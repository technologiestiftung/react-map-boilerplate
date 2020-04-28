# Mapbox React Filterable Map Boilerplate

> This project serves as a template to plot spatial data on a map.

## Getting started

Add a ```.env``` file with your mapbox token and style credentials in the root directory. Register at mapbox to get an access token. Add the following information:

```
REACT_APP_MAP_TOKEN={{MAPBOX_TOKEN}}
REACT_APP_MAP_STYLE={{MAPBOX_STYLE_URL}}
```

## How to setup the project

In order to get things running clone this repo to your machine and install all dependencies with ```npm i```.
The map expects data as a ```geojson``` format. Place your data in ```public/data/``` directory. It's expected to be named as ```data.geojson```.

Inside the root directory you find the ```config.js```. Here you are obliged to define *what* and *how* properties of your geojson are displayed.

It is necessary to define the following sections inside your ```config.js```:

## How is the config.js structured?

#### Mapbox settings

The ```map``` key sets the style, default center of map, zoom level, min zoom, max zoom and others and can be edited here.

> It isn't required to change anything here to run the map.

```
map: {
  mapCenter: [13.4124999, 52.5040961], // points towards Berlin
  mapZoom: [10],
  ...
}
```

#### Sidebar: About section

The about section of the app consists of a ```legend```, a ```title``` and a number of ```paragraphs``` you want to show to.

##### Legend

Based on the properties of each feature of your dataset you define what property should be distincted by color. Set the key ```id``` of the object ```legend``` in your config as one of the existing props in your dataset. For example:

```
// data.geojson
{
  "type": "FeatureCollection",
  "features": [
      {
        "type": "Feature",
        "geometry": ...
        "properties": {
            "some_property": 'nominal_value',
            ...
        }
      }
  ]
}

// config.js
about: {
  legend: {
    id: 'some_property'
  }
}
```

###### Title & paragraphs

...



1. Inside the **tooltip** (when hovering above an item on the map)
2. Inside the **detail** Section of the sidebar (which provides a more default view on available data of the selected item)
3. On the **about** section of the sidebar (which provides additional information about the project)

### tooltip & detail
- id -> Name of the key inside properties of each feature.
- component -> React component that is rendered.
- label -> Label that is displayed above the data.

#### Available components
- tags -> expects the data to be an **array of strings**
- openingHours -> expects the data to be an **array of objects**. Each object should have the following keys 
- title -> expects the data to be a **string**
- description -> expects the data to be a **string**
- link -> expects the data to be a **string**

```
  detail: [
    {
      id: "name",
      component: "title",
      label: "Institution",
    }
  ]
```

### about


```
  about: {
    title: "Name des Projekts hier",
    paragraphs: [
      {
        title: "Subheadline hier",
        content: "Lorem ipsum [dolorem](https://www.google.de) est.",
      },
      {
        title: "Subheadline hier",
        content: "Lorem ipsum [dolorem](https://www.google.de) est.",
      },
    ]
  },
```







Available Content types:

- title
- paragraph



This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (Webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `npm run build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify
