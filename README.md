# SkeletonAppDemo 

## With Skeleton View

<img width="1169" src="https://user-images.githubusercontent.com/47273077/156077979-20b45e45-d65d-4ece-861d-19c07870f569.png">

<img width="1157" src="https://user-images.githubusercontent.com/47273077/156078032-4e21e428-6d4d-498a-a6d3-a972cb568357.png">

<img width="1165" src="https://user-images.githubusercontent.com/47273077/156078119-fe7bad59-0c81-440f-9f4e-a861a94a8803.png">

<img width="1135" src="https://user-images.githubusercontent.com/47273077/156078185-0c469452-fcc7-441a-9ece-40d08f5bdcf2.png">

## Before:
```swift

import UIKit

class ViewController: UIViewController, UITableViewDataSource {
    
    @IBOutlet var tableView: UITableView!
    
    var data = [String]()

    override func viewDidLoad() {
        super.viewDidLoad()
        tableView.rowHeight = 120
        tableView.estimatedRowHeight = 120
        tableView.dataSource = self
        
        DispatchQueue.main.asyncAfter(deadline: .now() + 5, execute: {
            
            for _ in 0..<30 {
                self.data.append("Some text")
            }
            
            self.tableView.reloadData()
        })
    }
    
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return data.count
    }
    
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: MyTableViewCell.identifier, for: indexPath) as! MyTableViewCell
        
        if !data.isEmpty {
            cell.myLabel.text = data[indexPath.row]
            cell.myImageView.image = UIImage(systemName: "star")
        }
        
        return cell
    }


}

```
