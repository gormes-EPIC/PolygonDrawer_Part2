# Polygon Drawer: Part 2
[Video Link](https://drive.google.com/file/d/1MNcSKkSMabllnWRacDVSIHVTmxzsqfce/view?usp=sharing)

## Build the model 
1. Build out the `Model` class
	1. The way our application will work is each vertex will be of type `Polygon` from the default Java library. Each polygon you see on the screen will be drawn of type `Polygon` . Your  program will be able to draw multiple `Polygons` on the screen and deselect them when complete. 
	2. Using a data structure of your choice, create a collection of `Polygon` objects in your model.
	3. The only other instance variable is a "selected" vertex. This will be the most recently added vertex to the program
	4. Add methods to support the following functionality to your model
		1. Get the size
		2. Add a `Polygon` object
		3. Select the `Polygon` object passed in as a parameter
		5. Remove all `Polygon` objects
		6. Unselect the current `Polygon` object
		7. Get the currently selected `Polygon` object
		8. Check if the selected `Polygon` object is the selected one
		9. Returns an `Iterator` of all of the `Polygon` objects
## Update PolygonDrawer and Application
1. Add a `paintComponent(Graphics g)` method to `PolygonDrawer`. This will override the default `paintComponent` method from `JPanel`. This method should follow the following general logic.
	1. Run the super constructor
	2. Get the `Iterator` from the model
	3. For every `Polygon` in the list,
		1. Use the `drawLine()` method from the `Graphics` object to draw a line between each `Polygon` using its's `xpoints` and `ypoints` values
		2. If there are less than three `Polygon` objects, in the `Iterator`, then draw a small circle at the `Polygon` objects' location.
2. Update the `Application` class by adding a mouse listener to the `contentPane`
	1. Use the `addMouseListener(...)` method which will take a `MouseAdapter` object as a parameter. Override the `mouseClicked(MouseEvent e)` method of the `MouseAdapter`. You should be able to do this all in the same statement. `MouseEvent` objects have a method `getPoint()` which returns a `Point` object.

## AddPointController
1. Create your first controller class called `AddPointController` which needs the following attributes
	1. Instance variables for `Model` and `Application`
	2. A constructor to initialize those values as they are passed in
	3. The method `addPoint(Point p)` which will either add the vertex to the shape or create a new one as appropriate (and update the model). To add a vertex, use the `addPoint()` method for the selected vertex. `Point` objects have attributes `x` and `y`.
	4. You can refresh the application display by using the `repaint()` method that `Application` inherits from JFrame
2. Update the `mouseListener()` in `Application` to run the `AddPointController`. 
3. Run the whole thing! You should be able to have lines show up.


## UpdateMenuController
1. Create a controller to update the menu text based on the state of the model. It should have one method `updateModel(Application app, Model model)` which sets the text of the undo option as 'Remove Last Point' or 'Remove Last Polygon' as appropriate. It should also disable both the reset and undo menu items if no `Polygon` objects exist in the model. 
2. This controller should have one method `public static void updateMenu (Application app, Model model)` which uses the getters for both menu items and the `setEnabled(boolean)`, `setText(String)` to enable/disable the items and set the text as appropriate. 

## CompletePolygonController
1. Create `CompletePolgyonController` which marks the current `Polygon` as complete unselects the current `Polygon`.
2. This controller should have two instance variables `Model` and `Application`, the constructor `CompletePolygonController(Application app, Model m)`, and the method `complete()` which deselects the current `Polygon`, updates the menu items and repaints the screen to show the changes.

---
If you need a refresh on part 1, here is an updated video tutorial.
[Video Link](https://drive.google.com/file/d/1Af_SsyIIO5ylwIjyhPeLYX1E_zzrid2n/view?usp=sharing)
