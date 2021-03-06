Url: package-builder-announcements
Title: Chocolatey’s Package Builder Now With a UI and an Exciting New Feature!
Author: Rob Reynolds
Published: 20161115
Tags: package builder, news, press-release, chocolatey for business,video
Keywords: package builder, news, press-release, chocolatey for business, chocolatey, generate packages, dev ops, software deployment automation, software management automation, video
Summary: Package Builder has a new UI and can generate software deployments as packages from Programs and Features!
---

Chocolatey's Package Builder allows you to create fully ready to go software deployments for Windows in 5-10 seconds! There is nothing faster than Chocolatey when it comes to preparing software for an unattended deployment across your organization. Today we are excited to announce Package Builder UI and building packages directly from Programs and Features! Before we show you those features with some videos, let's reintroduce Package Builder as you may not be familiar.

### Chocolatey's Package Builder
Chocolatey’s Package Builder is a tool that allows you to quickly generate high quality packaging by pointing Package Builder to an installer (msi, exe, msu, or msp) or zip. You can create packages from your organization's archive of installers and zips, scripting the entire creation of packages for your organization. There are also nice features like MSI properties automatically being added to the installer comments so you can further customize the package!

We've created a short video showing how it works.

<iframe width="560" height="315" src="https://www.youtube.com/embed/6TXY5Ie-3wg" frameborder="0" allowfullscreen></iframe>

Quickly script out creating packages for your entire organization's cache of software, allowing you to completely automate your Windows installations in moments, not months. You can do that with a simple script:

~~~powershell
$path = '\\company.file.server\installers'


# Generate packages over supported types of files
$supportedTypes = @('.exe', '.msi', '.7z', '.zip', '.msu', '.msp')
Get-ChildItem -Path $path -Recurse | ?{
  $extension = [System.IO.Path]::GetExtension($_.Name)
  $supportedTypes.Contains($extension)
  } | %{
  Write-Host "$($_.FullName)"
  & choco new --file "$($_.FullName)" --build-package --outputdirectory $pwd
}
~~~

For every supported type, we are asking Chocolatey to wrap an entire package around the installer or zip, completely readying entire packages in about 5-10 seconds, complete with silent arguments. 

### Package Builder User Interface
Not every person is going to love the command line or may not be familiar with the command line. We've spent countless hours talking to customers and with their feedback we're introducing Package Builder UI. This also gives you an opportunity to transition from existing UI tools while taking advantage of powerful Chocolatey concepts!

<iframe width="560" height="315" src="https://www.youtube.com/embed/qJNKR_PEQqY" frameborder="0" allowfullscreen></iframe>

### Package Builder - Generate Packages From Programs and Features
Another way Package Builder can generate packages is based on looking at what is installed on a system in Programs and Features. You can set up a complete reference system and then use Chocolatey to generate packages from those installs. This gives you lightning quick ramp up time in both package and automating your Windows software installations!

<iframe width="560" height="315" src="https://www.youtube.com/embed/Mw_ReipnskI" frameborder="0" allowfullscreen></iframe>

### Chocolatey And Deployment Automation
When it comes to software management automation (or software deployment automation) for Windows, ask yourself if one or more of the following questions apply:

* Does your current approach to automation require manual interaction?
* Do the current processes you use feel inadequate or require work arounds? 
* Are you managing software for both internal applications and 3rd party software on Windows? If so, are your approaches consistent? 
* Can you update a single piece of software across your organization in less than 2 hours? 30 minutes? 5 minutes? 
* Does that time still apply from the moment you determine a need to upgrade to implementation?

Hundreds of organizations in every industry have seen the power of Chocolatey and have harnessed Chocolatey's Package Builder to create packages very quickly, allowing them to quickly address software deployments, security concerns, and just meeting their internal customer needs very quickly in a scalable and reliable way. Chocolatey will make a difference in your organization as well.

### Learn More

* Watch all videos related to [Chocolatey’s Package Builder](https://www.youtube.com/playlist?list=PLfn-TaDnc1us5X-PVlxW8M1h-6mXEXZSG "Chocolatey's Package Builder").
* Learn about other features available in [Chocolatey for Business](https://chocolatey.org/compare).
* [Contact us](https://chocolatey.org/contact) to find out more and setup your evaluation of Chocolatey for Business today.
