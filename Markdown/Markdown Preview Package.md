# Markdown Preview package

Show the rendered HTML markdown to the right of the current editor using `ctrl-shift-m`.

It can be activated from the editor using the `ctrl-shift-m` key-binding and is currently enabled for `.markdown`, `.md`, `.mdown`, `.mkd`, `.mkdown`, `.ron`, and `.txt` files.

![markdownPreview](https://cloud.githubusercontent.com/assets/378023/10013086/24cad23e-6149-11e5-90e6-663009210218.png)

# Customize

By default Markdown Preview uses the colors of the active syntax theme. Enable

- Use GitHub.com style

in the __package settings__ to make it look closer to how markdown files get rendered on github.com.

![markdownPreview2](https://cloud.githubusercontent.com/assets/378023/10013087/24ccc7ec-6149-11e5-97ea-53a842a715ea.png)

To customize even further, the styling can be overridden in your `styles.less` file. For example:
`
.markdown-preview.markdown-preview {
  background-color: #444;
}
`

I copied the contents and made it using markdown format from the following [page](https://github.com/atom/markdown-preview)
