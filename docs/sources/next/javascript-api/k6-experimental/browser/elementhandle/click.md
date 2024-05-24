---
title: 'click([options])'
description: 'Browser module: elementHandle.click method'
---

# click([options])

{{% admonition type="warning" %}}

Use [`locator.click([options])`](https://grafana.com/docs/k6/<K6_VERSION>/javascript-api/k6-experimental/browser/locator/click/) instead.

{{% /admonition %}}

Mouse click on the chosen element.

<TableWithNestedRows>

| Parameter           | Type     | Default | Description                                                                                                                                                                                                                                                                                                                                   |
| ------------------- | -------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| options             | object   | `null`  | Optional parameters.                                                                                                                                                                                                                                                                                                                          |
| options.button      | string   | `left`  | The mouse button (`left`, `middle` or `right`) to use during the action.                                                                                                                                                                                                                                                                      |
| options.clickCount  | number   | `1`     | The number of times the action is performed.                                                                                                                                                                                                                                                                                                  |
| options.delay       | number   | `0`     | Milliseconds to wait between `mousedown` and `mouseup`.                                                                                                                                                                                                                                                                                       |
| options.force       | boolean  | `false` | Setting this to `true` will bypass the actionability checks (`visible`, `stable`, `enabled`).                                                                                                                                                                                                                                                 |
| options.modifiers   | string[] | `null`  | `Alt`, `Control`, `Meta` or `Shift` modifiers keys pressed during the action. If not specified, currently pressed modifiers are used.                                                                                                                                                                                                         |
| options.noWaitAfter | boolean  | `false` | If set to `true` and a navigation occurs from performing this action, it will not wait for it to complete.                                                                                                                                                                                                                                    |
| options.position    | object   | `null`  | A point to use relative to the top left corner of the element. If not supplied, a visible point of the element is used.                                                                                                                                                                                                                       |
| options.position.x  | number   | `0`     | The x coordinate.                                                                                                                                                                                                                                                                                                                             |
| options.position.y  | number   | `0`     | The y coordinate.                                                                                                                                                                                                                                                                                                                             |
| options.timeout     | number   | `30000` | Maximum time in milliseconds. Pass `0` to disable the timeout. Default is overridden by the `setDefaultTimeout` option on [BrowserContext](https://grafana.com/docs/k6/<K6_VERSION>/javascript-api/k6-experimental/browser/browsercontext/) or [Page](https://grafana.com/docs/k6/<K6_VERSION>/javascript-api/k6-experimental/browser/page/). |
| options.trial       | boolean  | `false` | Setting this to `true` will perform the actionability checks without performing the action.                                                                                                                                                                                                                                                   |


</TableWithNestedRows>

### Returns

| Type            | Description                                                |
| --------------- | ---------------------------------------------------------- |
| `Promise<void>` | A Promise that fulfills when the click action is finished. |

### Examples

{{< code >}}

```javascript
import { browser } from 'k6/experimental/browser';

export const options = {
  scenarios: {
    browser: {
      executor: 'shared-iterations',
      options: {
        browser: {
          type: 'chromium',
        },
      },
    },
  },
};

export default async function () {
  const page = await browser.newPage();
  await page.goto('https://test.k6.io/browser.php');

  const button = await page.$('#counter-button');
  await button.click();

  page.close();
}
```

{{< /code >}}

When a click action results in a page navigation, remember to work with `Promise.all()` and `page.waitForNavigation()` to properly handle the asynchronous operation.

{{< code >}}

```javascript
import { browser } from 'k6/experimental/browser';

export const options = {
  scenarios: {
    browser: {
      executor: 'shared-iterations',
      options: {
        browser: {
          type: 'chromium',
        },
      },
    },
  },
};

export default async function () {
  const page = await browser.newPage();
  await page.goto('https://test.k6.io/');

  const messagesLink = await page.$('a[href="/my_messages.php"]');

  await Promise.all([
    page.waitForNavigation(),
    messagesLink.click()
  ]);

  page.close();
}
```

{{< /code >}}