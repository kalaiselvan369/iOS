## Size & Orientation

iPhone sizes are measured in terms of points(mathematically) and pixels. 

For example iPhone 2G and 3G has 320 x 480 points and rendered at 1x -> 320x480 pixels. This means 1 point 
can accomodate one pixel.

Likewise, iPhone 4 and 4s has 320 x 480 points and rendered at 2x -> 640 x 960 pixels. This means each point 
can accomodate two pixels.

## Auto layout tools

1. Stack
2. Align
3. Pin
4. Resolve auto layout issues automatically

## Inspectors

1. Size Inspector
2. Attribute Inspector
3. Identity Inspector

## Pinning

Pinning allow us to set a view position in relation to the other view position.

## Alignment

Align a view either horizontally, vertically or both.

## Containers

It is UIView which allow us to add sub views.

## Stack Views

Arrange view in horizontal stack or vertical stack

## Adding different constraints to the button

1. Click on the constraint option
2. Set the height or width 
3. Click on Add

Every time you do the above step on the same button it will add different constraints like
equal to, less than or equal to, greater than of equal to.


## Creating custom view controller that load view without story board

To call one view controller(in our case it is custom view controller) from another view controller 

```swift

 let customViewController = CustomViewController()
 customViewController.bmi = String(bmi) // assing value to the property in custom view controller
 self.present(customViewController, animated: true, completion: nil)

```

## Custom View Controller

Custom view controller doesn't use the views declared in the story board. Instead it create its own
view programmaticaly. Like android custom view which draw on x,y coordinates.


![image](../assets/customviewcontroller.png)

The above image shows difference between the story board and custom view controllers. Use either story board and create outlets
or create views programmatically in the view controller class.

> Creating custom views and custom view controllers are tedious process

## Cocopod touch class & Tag the ViewController to Story board

If we have to navigate from one view controller to another view controller, then we can make use cocopod touch class 
and `segue` to create a navigation link from one view controller to another view controller from the storyboard. 

1. Create a view controller class using cocopod touch class
2. Click on the specific storyboard and assign the ViewController class in the right side menu section.

### Creating Segue

1. Link two view controller by `segue`
2. Once you define the segue, set the identifier for the segue
3. make use of the identifier key to navigate from one view controller to another

> Note: While adding identified in the segue, to the below don't add the class linker. Just leave it empty

We can use **Present Modally** in Seque options for now.

```swift
 self.performSegue(withIdentifier: "goToResult", sender: self)
```

In case you have to pass some data before the result view controller loads up then we have
to override the below function `prepare` in the sender/caller

```swift
override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
    if(segue.identifier == "goToResult") {
        let resultViewController = segue.destination as! ResultViewController            
        resultViewController.bmi = "9.0" // setting the value for bmi in the result view controller
    }
}
```

## Support Dark mode

1. By default, if use system colors for the labels, images, etc., the os will set the adaptive color when we
   switch to light or dark mode
2. If we need custom color in lables, or in other assets then in Assets.xcassets folder, we have to specify that
   custom color along with light mode and dark mode colors so that when user to switch dark mode we have seemless UI/UX.
3. Using scalar assets like PNG, JPEG is not much effective since when we zoom the picture gets blurred.
4. Using vector assets is an advantage because even when we zoom we won't loose clarity
5. We can use image.pdf as a vector assets also. 
6. In order to use vectors(.pdf in assets) set scale to `Single Scale`, enable `Preserve Vector Data`, appearances `Any, Light, Dark`


## UITextFieldDelegate

```swift
import UIKit

class WeatherViewController: UIViewController, UITextFieldDelegate {

    @IBOutlet weak var conditionImageView: UIImageView!
    @IBOutlet weak var temperatureLabel: UILabel!
    @IBOutlet weak var cityLabel: UILabel!
    
    @IBOutlet weak var searchTextField: UITextField!
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.

        // this is similar to setOnClickListeners in android -- important to set this
        searchTextField.delegate = self
    }
    
    @IBAction func searchButtonPressed(_ sender: UIButton) {
        searchTextField.endEditing(true)
        print(searchTextField.text!)
    }
 
    // frameworks call this function -- by delegate
    // when return key is pressed then do some action
    func textFieldShouldReturn(_ textField: UITextField) -> Bool {
        searchTextField.endEditing(true)
        print(searchTextField.text!)
        return true
    }
    
     // frameworks call this function -- by delegate
    func textFieldShouldEndEditing(_ textField: UITextField) -> Bool {
        if textField.text != nil {
            print(searchTextField.text!)
            return true
        } else {
            textField.placeholder = "Type something"
            return false
        }
    }
    
     // frameworks call this function -- by delegate
     // we editing is done and keyboard is closed
    func textFieldDidEndEditing(_ textField: UITextField) {
        textField.text = ""
    }

}

```

## Execute Code in UI Thread / Main Thread

```swift
DispatchQueue.main.async {
    
}
```

## Extending UIKit

```swift
extension UIButton {
    
    func makeCircular() {
        self.clipsToBounds = true
        self.layer.cornerRadius = self.frame.size.width / 2
    }
}

let button = UIButton.init(frame: CGRect.init(x: 0, y: 0, width: 50, height: 50))
button.backgroundColor = UIColor.red
button.makeCircular()
```

## Segregation Delegates by avoiding noise in single class

Here we are creating extension for View Controller class. Since we can implement protocols to 
extension Class hence we refactored our code.

```swift
// MARK: - Extending WeatherView Controller for UITextFieldDelegate

extension WeatherViewController : UITextFieldDelegate {
    
    @IBAction func searchButtonPressed(_ sender: UIButton) {
        searchTextField.endEditing(true)
        manager.performRequest(url: manager.baseUrl)
        print(searchTextField.text!)
    }

    func textFieldShouldReturn(_ textField: UITextField) -> Bool {
        searchTextField.endEditing(true)
        manager.performRequest(url: manager.baseUrl)
        print(searchTextField.text!)
        return true
    }
    
    func textFieldShouldEndEditing(_ textField: UITextField) -> Bool {
        if textField.text != nil {
            print(searchTextField.text!)
            return true
        } else {
            textField.placeholder = "Type something"
            return false
        }
    }
    
    func textFieldDidEndEditing(_ textField: UITextField) {
        textField.text = ""
    }
}

//MARK: - Extending WeatherViewController for WeatherDelegate

extension WeatherViewController : WeatherDelegate {
    
    func weatherDidLoad(_ weatherManager: WeatherManager, model: WeatherModel) {
        DispatchQueue.main.async {
            self.temperatureLabel.text = model.temperatureInCelcius
        }
    }
    
    func weatherLoadingFailed(_ weatherManager: WeatherManager, error: Error) {
        print("faced error")
    }
}
```

## UIPicker View 

```swift
extension ViewController: UIPickerViewDataSource, UIPickerViewDelegate {
    func numberOfComponents(in pickerView: UIPickerView) -> Int {
        return 1
    }
    
    func pickerView(_ pickerView: UIPickerView, numberOfRowsInComponent component: Int) -> Int {
        return coinManager.currencyArray.count
    }
    
    func pickerView(_ pickerView: UIPickerView, titleForRow row: Int, forComponent component: Int) -> String? {
        return coinManager.currencyArray[row]
    }
    
    func pickerView(_ pickerView: UIPickerView, didSelectRow row: Int, inComponent component: Int) {
        let currency = coinManager.currencyArray[row]
        coinManager.getCurrencyValue(for: currency)
    }
}
```

Also in view controller we have set the delegate as 

```swift
 currencyPicker.dataSource = self // data source
 currencyPicker.delegate = self // view delegate usual delegate
```

## Core Location

1. To access core location we have to import core location module
2. Instantiate core location manager
3. set the location manager delegate
4. use core location manager object to request permission
5. Update the plist with all the location privay related key and value
6. use core location manager to request one time location update
7. once one time location is received, **stop location update**
8. we need one more one time location update then request location again.

## Navigation Controller

1. First click on the root/entry point/ main view controller
2. Go to Editor and choose embed in Navigation controller.
3. Finally the other view controllers which are linked main view controller via segue will get the back navigation icon

### Lot of stuffs with Navigation Controller

1. What if we have to pop to root view controller?

```swift
 navigationController?.popToRootViewController(animated: true)
```

2. What if we want to hide back button?

```swift
override func viewDidLoad() {
    super.viewDidLoad()
    navigationItem.hidesBackButton = true
}
    
```

3. What if we want to set title to the nav bar??

```swift
override func viewDidLoad() {
    super.viewDidLoad()
    title = "⚡️FlashChat"
}    
```

4. How do you hand button in the nav bar???

We have to use UIBar button.


## Table View

Things involved in implementing table view:

1. Table view
2. Table view cell (Protype cell) -- 
3. **Specifying reuse identifier in story board for the prototype is important**
4. Extend UITable view data source for the data 


```swift
extension ChatViewController : UITableViewDataSource {
    
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        messages.count
    }
    
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(
            withIdentifier: Constant.CELL_IDENTIFIER_CHAT_ITEM,
            for: indexPath)
        cell.textLabel?.text = messages[indexPath.row].body
        return cell
    }
}
```

### Customizing table view cell

In the above example, for the table view we have set the cell which is available in the story board by default. 
What if we want to customize the cell. In that case we have to create our own new UITableViewCell.

1. Create new file under view directory
2. Choose cocoapod touch class 
3. Choose parent class as UITableViewCell and choose the file name as MessageCell
4. **Check for .xib file also** This is the file where we edit our UI elements like we do in storyboard
5. Click Done

Now you can see two files created namely MessageCell(swift) and MessageCell(storyboard).

The storyboard related class has all the capabilities that we used to do for usual storyboard.

```swift

class MessageCell: UITableViewCell {

    @IBOutlet weak var content: UILabel!
    @IBOutlet weak var avatarImage: UIImageView!
    @IBOutlet weak var messageBubble: UIView!
    
    override func awakeFromNib() {
        super.awakeFromNib()
        // Initialization code -- this is like onViewLoadFunction
        messageBubble.layer.cornerRadius = CGFloat.init(10.0)
    }

    override func setSelected(_ selected: Bool, animated: Bool) {
        super.setSelected(selected, animated: animated)

        // Configure the view for the selected state
    }
}

```

Now we can the remove the default(prototype) cell which we had in the table view of the chat view controller storyboard. 
Since we are having custom message cell & message storyboard(.xib), we have to register it to the table view in onViewLoad()

```swift
 tableView.register(
            UINib.init(nibName: "MessageCell", bundle: nil),
            forCellReuseIdentifier: Constant.CELL_IDENTIFIER_CHAT_ITEM
)
```

Also **casting** to the new custom Message cell is very important

```swift
extension ChatViewController : UITableViewDataSource {
    
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        messages.count
    }
    
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(
            withIdentifier: Constant.CELL_IDENTIFIER_CHAT_ITEM,
            for: indexPath) as? MessageCell
        cell?.content?.text = messages[indexPath.row].body
        return cell!
    }
}
```



