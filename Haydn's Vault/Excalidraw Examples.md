# Embedding Excalidraw Drawings

There are several ways to embed Excalidraw drawings in your notes:

## 1. Direct Embedding
You can embed an Excalidraw drawing directly in your note using this syntax:
```excalidraw
{
  "type": "excalidraw",
  "version": 2,
  "source": "https://excalidraw.com",
  "elements": [
    {
      "type": "rectangle",
      "version": 1,
      "versionNonce": 1,
      "id": "example",
      "x": 100,
      "y": 100,
      "width": 100,
      "height": 100,
      "angle": 0,
      "strokeColor": "#000000",
      "backgroundColor": "#ffffff",
      "fillStyle": "solid",
      "strokeWidth": 1,
      "strokeStyle": "solid",
      "roughness": 1,
      "opacity": 100,
      "groupIds": []
    }
  ]
}
```

## 2. Linking to Existing Drawings
You can link to existing Excalidraw files with different widths and padding:

Default size:
![[Excalidraw/Excalidraw Examples 2025-06-16 16.01.58.excalidraw]]

500 pixels wide:
![[Excalidraw/Excalidraw Examples 2025-06-16 16.01.58.excalidraw|500]]

50% of container width:
![[Excalidraw/Excalidraw Examples 2025-06-16 16.01.58.excalidraw|50%]]

With padding (using CSS):
<div style="padding: 20px; background-color: #f5f5f5; border-radius: 8px;">
![[Excalidraw/Excalidraw Examples 2025-06-16 16.01.58.excalidraw|400]]
</div>

With custom styling:
<div style="padding: 30px; margin: 20px; background-color: #e8f4f8; border: 2px solid #4a90e2; border-radius: 12px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
![[Excalidraw/Excalidraw Examples 2025-06-16 16.01.58.excalidraw|300]]
</div>

## 3. Creating New Drawings
To create a new drawing:
1. Use the command palette (Ctrl/Cmd + P)
2. Type "Excalidraw: New drawing"
3. Or click the Excalidraw icon in the ribbon

## Tips
- Drawings are stored as `.excalidraw.md` files
- You can edit drawings directly in the note
- Use the Excalidraw plugin settings to customize the experience
- Control image width using `|width` syntax (e.g., `|500` for pixels or `|50%` for percentage)
- Add padding and styling using HTML/CSS div containers
- Common CSS properties for styling:
  - `padding`: Space inside the container
  - `margin`: Space outside the container
  - `background-color`: Background color
  - `border-radius`: Rounded corners
  - `box-shadow`: Add shadow effects
  - `border`: Add borders

#excalidraw #tutorial 