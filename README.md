# react-media-resize
Adaptive React components with a callback on entering or leaving in particular browser width on resize.

## Install

```console
$ npm install --save react-media-resize
```

## API

### `<MediaRange />`
The component that present possibility to work with responsive design in ReactJS.
It let us to use different components and change component state witch depends from browser screen width (on window resize).

#### Props

- `range` (*String or array*): Range with width or array of ranges. 
- `onEnter` (*Function*): Callback for entering in particular browser width
- `onLeave` (*Function*): Callback for leaving from particular browser width

## Component Usage
```javascript
import React from 'react';
import MediaRange from 'react-media-resize';

export default class App extends React.Component {
    handlerEnterWidth() {
        console.log('You entered in range 768..1024');
    }
    
    handlerLeaveWidth() {
        console.log('You left range 768..1024');
    }
    
    render(
        <MediaRange
          range="768..1024"
          onEnter={this.handlerEnterWidth}
          onLeave={this.handlerLeaveWidth}
         >
           <AnotherComponent />
        </MediaRange>
    )
}
```

You can also use several ranges for different window sizes with own callbacks:
```javascript
import React from 'react';
import MediaRange from 'react-media-resize';

export default class App extends React.Component {
    render() {
        const rangesList = [
            {
                range: '..480',
                onEnter: () => {
                  console.log('Entered in mobile width');
                }
            },
            {
                range: '481..1024',
                onEnter: () => {
                  console.log('Entered in tablet width');
                },
                onLeave: () => {
                  console.log('Left tablet width');
                }
            },
            {
                range: '1025..',
                onEnter: () => {
                  console.log('Entered in desctop screen width');
                }
            }
        ];
    
        return (
            <MediaRange range={rangesList}>
               <AnotherComponent />
            </MediaRange>
        )
    }
}
```

Also we can include to render or exclude component on window resize:
```xml
<MediaRange>
   <AnotherComponent range="..479" />
   <AnotherComponent range="480..1200" />
   <AnotherComponent range="480..960" />
   <AlwaysVisibleComponent />
   <AnotherComponent range="1200.." />
</MediaRange>
```