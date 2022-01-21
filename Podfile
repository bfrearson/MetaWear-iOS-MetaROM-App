# Uncomment the next line to define a global platform for your project
platform :ios, '14.0'
use_frameworks!

def all_pods
  pod 'MetaWear', :subspecs => ['UI', 'AsyncUtils']
  pod 'MBProgressHUD'
  pod 'Charts'
  pod 'IQKeyboardManagerSwift'
  pod 'CircularSlider'
  pod 'Instructions'
  pod 'RealmSwift'
  pod 'Zip'
  pod 'RMessage'
end

target 'MetaRom' do
  all_pods
  target 'MetaRomTests' do
    inherit! :search_paths
    pod 'Fakery'
  end
end

pre_install do |installer|
  installer.analysis_result.specifications.each do |s|
    s.swift_version = '4.2' unless s.swift_version
  end
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
    # some older pods don't support some architectures, anything over iOS 11 resolves that
      config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '14.0'
    end
  end
end
