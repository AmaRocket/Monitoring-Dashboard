# System Monitoring Dashboard

![Screenshot from 2025-05-15 17-49-44.png](Screenshot%20from%202025-05-15%2017-49-44.png) Dashboard example

A responsive, interactive dashboard for monitoring various system services and metrics in real-time. The dashboard features draggable and resizable panels, layout persistence, and automatic refresh functionality.

## Features

- **Draggable Panels**: Each monitoring panel can be dragged and repositioned anywhere on the screen
- **Resizable Panels**: Panels can be resized using the bottom-right corner
- **Layout Persistence**: Save and restore panel layouts using local storage
- **Auto-Refresh**: Automatic refresh of all monitoring panels every 5 minutes
- **Fullscreen Mode**: Automatically enters fullscreen mode on load
- **Responsive Design**: Adapts to different screen sizes

## Monitored Services

- MAAS Cluster Statistics
- HPC Cluster Status
- Nagios System Monitoring
- Temperature Plots
- ALIS2 Status (Custom management system)
- Ultimaker Status (using Docker container to use it as an Iframe: command bellow)

```docker run -it -d -p 3000:3000 --restart unless-stopped linuxserver/firefox:latest ```

## Technical Details

### Panel Structure
Each monitoring panel is contained within an iframe container with the following features:
- Drag handle at the top
- Panel name label
- Resizable corners
- Border highlighting on hover

### Layout Management
- **Save Layout**: Stores the current position and size of all panels
- **Restore Layout**: Returns panels to their saved positions and dimensions
- Layouts are stored in the browser's localStorage

### Refresh Mechanism
Each service has its own refresh function running on a 5-minute interval:
- `clusterReload()`: Refreshes HPC cluster status
- `maasReload()`: Updates MAAS cluster statistics
- `tempReload()`: Refreshes temperature plots
- `alisReload()`: Updates ALIS2 status
- `nagiosReload()`: Refreshes Nagios monitoring
- `ultimakerReload()`: Updates Ultimaker status

## Usage

1. Open the dashboard in a web browser
2. Drag panels to desired positions using the top bar of each panel
3. Resize panels by dragging the bottom-right corner
4. Use the control bar buttons to:
   - Save current layout
   - Restore previous layout

## Browser Requirements

- Modern web browser with JavaScript enabled
- Support for CSS Grid and Flexbox
- Local storage enabled for layout persistence
- Fullscreen API support

## Security Notes

- Ensure proper access controls are in place for monitored services
- Some services may require authentication
- Local file access (for temperature plots) requires appropriate permissions

## Customization

The dashboard can be customized by:
- Adjusting refresh intervals in the JavaScript code
- Modifying the grid layout in CSS
- Adding or removing monitoring panels
- Changing panel styles in the CSS

## Troubleshooting

If panels are not refreshing:
1. Check network connectivity to services
2. Verify service endpoints are accessible
3. Ensure browser security settings allow iframe content
4. Check browser console for potential errors

## Development

To modify or extend the dashboard:
1. Edit the HTML structure for new panels
2. Adjust CSS for styling changes
3. Modify JavaScript for new functionality
4. Test thoroughly in target environment