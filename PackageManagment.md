## Set up POD

1. In terminal run sudo gem install cocoapods
2. Navigate to iOS project root directory using terminal
3. Run pod init
4. Open the pod file using text editor 
5. Modify the iOS version as needed
6. Add the pod inside the pod file
7. Save and close the file
8. Run pod install in the same terminal
9. Use project.xcodeworkspace form now to open the project


```ruby

platform :ios, '13.0'

target 'Flash Chat iOS13' do
  use_frameworks!

  # Pods for Flash Chat iOS13
  pod 'CLTypingLabel', '~> 0.4.0'

end

```

## Remove pod

1. Delete the particular pod in the pod file
2. From terminal run pod install from the root directory of the project 

## Podfile.lock 

Gives detail information about the cocoapod version and pod versions installed

Here is the sample 

```yaml
PODS:
  - CLTypingLabel (0.4.0)

DEPENDENCIES:
  - CLTypingLabel

SPEC REPOS:
  trunk:
    - CLTypingLabel

SPEC CHECKSUMS:
  CLTypingLabel: 95a7d1faf7e3d1d952cd11cb0491d17d80c50934

PODFILE CHECKSUM: e027b2617b34aff7a1197acd56d70c42047f182f

COCOAPODS: 1.12.1

```