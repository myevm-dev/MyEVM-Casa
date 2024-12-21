#MyEVM CASA

to be added

   "Soon-Art": [
      {
        name: "Art",
        image: "/images/soon.png",
      },
    ],
    "Soon-Start": [
      {
        name: "Start",
        image: "/images/soon.png",
      },
    ],
    "Soon-Games": [
      {
        name: "Games",
        image: "/images/soon.png",
      },
    ],
    "Soon-Life": [
      {
        name: "Life",
        image: "/images/soon.png",
      },
    ],
    "Soon-Data": [
      {
        name: "Data Markets",
        image: "/images/soon.png",
      },
    ],
    "Soon-Shop": [
      {
        name: "Shop",
        image: "/images/soon.png",
      },
    ],
    "Soon-Biz": [
      {
        name: "Biz",
        image: "/images/soon.png",
      },
    ],
        "TheToken": [
      {
        name: "TheToken",
        image: "/images/soon.png",
      },
    ],

      "Art-Demo": [
      {
        name: "NFT Marketplace ",
        image: "/images/artlogo.png",
        code: "https://github.com/myevm-dev/",
        url: "https://myevm.art",
      },
    ],
            {
        name: "MyEVM Start on X.com",
        url: "https://x.com/myevmstart",
        image: "/images/x.png",
      },
      {
        name: "MyEVM Win on X.com",
        url: "https://x.com/myevmwin",
        image: "/images/x.png",
      },
      {
        name: "MyEVM Data on X.com",
        url: "https://x.com/myevmdata",
        image: "/images/x.png",
      },
      {
        name: "MyEVM Games on X.com",
        url: "https://x.com/myevmgames",
        image: "/images/x.png",
      },
      {
        name: "MyEVM Media on X.com",
        url: "https://x.com/myevmmedia",
        image: "/images/x.png",
      },
            {
        name: "MyEVM Casa on X.com",
        url: "https://x.com/myevmcasa",
        image: "/images/x.png",
      },
            {
        name: "MyEVM Vip on X.com",
        url: "https://x.com/myevmvip",
        image: "/images/x.png",
      },
            {
        name: "MyEVM Biz on X.com",
        url: "https://x.com/myevmbiz",
        image: "/images/x.png",
      },
      {
        name: "MyEVM Pro on X.com",
        url: "https://x.com/myevmpro",
        image: "/images/x.png",
      },

We add sites and categories mainly to [database.js](src/database.js). 

There are up to 5 properties you can specify for each site: 

```
{
          name: "Site/Project/Design Name",
          url: "https://example.com",
          code: 
          image: "/images/{category}-{number}.webp",
          gif: "/images/{category}-{image-number}.webp",
},
```

### Keep in mind
1. The `name`, `url`, and `image` are mandatory. `code` and `gif` are optional. 
2. You can add it if there is an existing implementation of the design on CodePen or similar sites. If you're making one yourself, you can add the link there too.
3. You can add the images to `public/images`. 
4. There is a naming convention for images too: {category}-{number}.webp
The number follows the last existing image number. If you're adding the first site in a category, e.g., grainy, then it'd be grainy-1.webp, followed by grainy-2.webp, and so on.
5. A GIF is added when it's helpful to show a preview animation of the element. It must have the same number as the image followed by letter 'g', e.g., image-1g.webp. This GIF will show in the modal only.
6. Image should perfectly capture the element (200x344).
7. GIF should be as short as possible, only capturing the main effect/animation, so the file should not exceed 10MB.

