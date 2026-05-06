platform :osx, "11.0"

source 'https://github.com/MacDownApp/cocoapods-specs.git'  # Patched libraries.
source 'https://cdn.cocoapods.org/'

project 'MacDown.xcodeproj'

inhibit_all_warnings!

target "MacDown" do
  pod 'handlebars-objc', '~> 1.4'
  pod 'hoedown', '~> 3.0.7', :inhibit_warnings => false
  pod 'JJPluralForm', '~> 2.1'
  pod 'LibYAML', '~> 0.1'
  pod 'M13OrderedDictionary', '~> 1.1'
  pod 'MASPreferences', '~> 1.3'

  # Keep the current API surface until preferences are migrated away.
  pod 'PAPreferences', '~> 0.4'
end

target "MacDownTests" do
  pod 'PAPreferences', '~> 0.4'
end

target "macdown-cmd" do
  pod 'GBCli', '~> 1.1'
end

post_install do |installer|
  installer.generated_projects.each do |project|
    project.targets.each do |target|
      target.build_configurations.each do |config|
        config.build_settings['MACOSX_DEPLOYMENT_TARGET'] = '11.0'
        config.build_settings['ARCHS'] = '$(ARCHS_STANDARD)'
        config.build_settings['ONLY_ACTIVE_ARCH'] = 'NO'
        config.build_settings.delete('VALID_ARCHS')
        config.build_settings.delete('EXCLUDED_ARCHS')
        config.build_settings.delete('EXCLUDED_ARCHS[sdk=macosx*]')
      end
    end
  end
end
