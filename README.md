# QWebcamWidget
Convenient Qt widget for remote webcam connections that handles connection timeouts, invalid frame states and connection retries. 

## Example
``` C++
  m_webcamFrame = new QWebcamWidget(m_webcamUrl, 10000, this);
  m_webcamFrame->resize(size);
  m_webcamFrame->setSizePolicy(QSizePolicy::Expanding, QSizePolicy::Expanding);

  m_layout->addWidget(m_webcamFrame, 0, 0, 1, 3, Qt::AlignCenter);
  m_webcamFrame->play();
```

You can also set the icon displayed in the overlay for the individual printer states
``` C++
  m_webcamFrame->setStateIcon(
    QWebcamSource::State(QWebcamSource::Connected | QWebcamSource::Connecting),
    Settings::getThemeIcon("no-video")
    );

  m_webcamFrame->setStateIcon(
    QWebcamSource::State(QWebcamSource::Paused),
    Settings::getThemeIcon("pause")
    );

  m_webcamFrame->setStateIcon(
    QWebcamSource::State(QWebcamSource::Timeout | QWebcamSource::NoConnection | QWebcamSource::None | QWebcamSource::InvalidFrame),
    Settings::getThemeIcon("no-video")
    );
```
