# Unity-OBS Alpha Workflow Sample (URP)

![GIF](https://github.com/user-attachments/assets/897c2ec6-a8ff-425e-a032-ef81f698bd13)

This Unity sample project demonstrates how to blend Unity renders in OBS by
using inter-app frame interchange protocols such as Spout or NDI. It relies on
URP's alpha-channel output, so chroma keying (green background) is unnecessary.

It uses the following packages:

- KlakSpout (Windows)
- KlakNDI (Windows/Mac)

Although both are included for demonstration, choose whichever suits your
project.

## Key Points for Workflow Setup

- Set a camera render target to a Render Texture that supports alpha (for
  example, R8G8B8A8_SRGB). A Game View sender won't work because it lacks
  alpha data.
- Enable the "Alpha Processing" switch in the Universal Render Pipeline asset
  if you rely on post-processing.
- In Spout/NDI sender components, use the "Texture" capture method with that
  render texture and enable "Keep Alpha".

## Notes about Post-processing

- Bloom is discouraged because it has no influence on the alpha channel, so
  results are rarely desirable.
- If you're unsure about tonemapping, disable it, especially for
  non-photorealistic rendering.
- Use the [AlphaBypass] hack only when alpha interference in post-processing
  becomes a problem.

[AlphaBypass]: https://github.com/keijiro/URP-AlphaBypass
