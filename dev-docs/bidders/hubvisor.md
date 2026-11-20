---
layout: bidder
title: Hubvisor
description: Prebid Hubvisor Bidder Adapter
biddercode: hubvisor
pbjs: true
pbs: false
gvl_id: 1112
tcfeu_supported: true
usp_supported: true
gpp_sids: tcfeu, usnat, usstate_all, usp
coppa_supported: true
dsa_supported: true
schain_supported: true
dchain_supported: false
userIds: all
media_types: banner, video
deals_supported: true
floors_supported: true
fpd_supported: true
multiformat_supported: will-bid-on-any
prebid_member: true
sidebarType: 1
---

## Note

The Hubvisor adapter supports banner and video (instream and outstream) media types.

The adapter requires setup before beginning. Please contact [prebid@hubvisor.io](mailto:prebid@hubvisor.io) for setup and to obtain a placement ID.

## Bid Params

{: .table .table-bordered .table-striped }

| Name                | Scope    | Description                                                    | Example                 | Type     |
|---------------------|----------|----------------------------------------------------------------|-------------------------|----------|
| `placementId`       | optional | Hubvisor placement ID, provided by Hubvisor.                   | `'my-placement-id'`     | `string` |
| `video.maxWidth`    | optional | Outstream only. Maximum width of the player, in pixels.        | `640`                   | `number` |
| `video.targetRatio` | optional | Outstream only. Aspect ratio of the player.                    | `16 / 9`                | `number` |
| `video.selector`    | optional | Outstream only. CSS selector of the element hosting the player. | `'#my-video-container'` | `string` |

```javascript
const adUnits = [
  {
    code: 'div-prebid-banner',
    mediaTypes: {
      banner: {
        sizes: [[300, 250], [300, 600]]
      }
    },
    bids: [
      {
        bidder: 'hubvisor',
        params: {
          placementId: 'my-placement-id'
        }
      }
    ]
  }
];
```

### Example outstream ad unit

```javascript
const adUnits = [
  {
    code: 'div-prebid-outstream',
    mediaTypes: {
      video: {
        context: 'outstream',
        playerSize: [[640, 360]],
        mimes: ['video/mp4'],
        protocols: [2, 3, 5, 6],
        playbackmethod: [2]
      }
    },
    bids: [
      {
        bidder: 'hubvisor',
        params: {
          placementId: 'my-outstream-placement-id',
          video: {
            maxWidth: 640,
            targetRatio: 16 / 9
          }
        }
      }
    ]
  }
];
```
