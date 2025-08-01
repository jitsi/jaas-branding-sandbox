# Advanced Branding Sandbox for JaaS

This is a simple web UI that helps JaaS integrators preview and adjust advanced branding settings for their meetings.

## 🚀 How It Works

JaaS meetings can be customized through a branding configuration JSON file served from a URL you control.

The layout uses an embedded iFrame and form to let you:

* Choose your **Tenant ID**
* Choose a **Room name**
* (Optionally) add a JWT
* (Optionally) use the `stage.8x8.vc` environment


## ⚙️ Step-by-Step: Hosting and Using Your Branding JSON

### 1. Create Your JSON Configuration

Start with a file like this:

```json
{
  "backgroundColor":"#FFF",
  "logoClickUrl":"https://8x8.vc",
  "avatarBackgrounds": ["#12A378", "linear-gradient(125.83deg, #000 0%, #FFF 99.09%)"],
  "customTheme": {
    "palette": {
      "ui01": "orange !important",
      "action01": "green",
      "action01Hover": "lightgreen",
      "action02Disabled": "beige"
    },
    "typography": {
      "labelRegular": {
        "fontSize": 25,
        "lineHeight": 30,
        "fontWeight": 500
      }
    }
  }
}
```

The JSON should follow the schema shown in the official documentation. See the full list of supported properties here:
👉 [Advanced Branding options](https://developer.8x8.com/jaas/docs/jaas-prefs-advanced-branding#example-configuration)

### 2. Host Your Branding JSON

You need to host your branding JSON on a public HTTPS endpoint that meets the following requirements:

* Uses **HTTPS**
* Sets appropriate **CORS headers** (e.g., `Access-Control-Allow-Origin: *` or your tenant domain)
* Returns a **`Content-Type`** of `application/json`

Some popular options:

#### ✅ GitHub Pages

1. Create a new GitHub repo
2. Add your `branding.json` file
3. Enable GitHub Pages and copy the raw URL

  ```
  https://yourusername.github.io/repo-name/branding.json
  ```

#### ✅ Pipedream (easy and fast)

1. Go to [https://pipedream.com](https://pipedream.com)
2. Create a new **HTTP source**
3. In the workflow, use a `Respond with JSON` block and paste your config
4. Deploy and copy the HTTPS URL of the endpoint

Your branding JSON will now be available at:

```
https://xxxxxxx.m.pipedream.net/
```
### 3. Register the URL in the JaaS Console

This step is **required**: configure your custom branding in the JaaS admin interface.

1. Go to [https://jaas.8x8.vc](https://jaas.8x8.vc) or [https://jaas-pilot.8x8.vc](https://jaas-pilot.8x8.vc) for stage
2. Log in with your account
3. Navigate to **Branding → Advanced Branding**
4. Paste the URL of your `branding.json`
5. Save the configuration

Once saved, the branding will be applied automatically when you join a meeting with your tenant.

## 🧪 Tips

* Always test your branding URL in an incognito window to avoid cache.
* If hosting from GitHub or Pipedream, ensure proper CORS headers are set.
* If your endpoint response fails to load, the meeting will silently fall back to default branding.

## 📹 Need Help?

Watch the [official walk-through video](https://developer.8x8.com/jaas/docs/jaas-prefs-advanced-branding) for detailed instructions and examples.
