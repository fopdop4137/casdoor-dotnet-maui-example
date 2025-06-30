# Casdoor .NET MAUI Example: Authentication Made Simple 🌐🔐

![License](https://img.shields.io/badge/license-MIT-blue.svg) ![Version](https://img.shields.io/badge/version-1.0.0-green.svg) ![Release](https://img.shields.io/badge/releases-latest-orange.svg)

Welcome to the **casdoor-dotnet-maui-example** repository! This project showcases a .NET MAUI application and library that integrates with Casdoor for authentication. The goal is to provide a clear and practical example of how to implement authentication in your .NET MAUI applications using Casdoor's powerful features.

## Table of Contents

- [Features](#features)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Usage](#usage)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)
- [Links](#links)

## Features

- **Easy Authentication**: Implement authentication quickly with Casdoor.
- **Multiple Protocols**: Supports OAuth, OIDC, and SAML.
- **Identity Management**: Manage user identities seamlessly.
- **Cross-Platform**: Works on iOS, Android, and Windows.
- **Comprehensive Examples**: Includes practical examples for quick setup.

## Technologies Used

- .NET MAUI
- C#
- Casdoor
- OAuth 2.0
- OpenID Connect (OIDC)
- SAML
- Casbin for authorization

## Installation

To get started with this project, follow these steps:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/fopdop4137/casdoor-dotnet-maui-example.git
   ```

2. **Navigate to the Project Directory**:
   ```bash
   cd casdoor-dotnet-maui-example
   ```

3. **Install Dependencies**:
   Make sure you have .NET 6 or later installed. Run:
   ```bash
   dotnet restore
   ```

4. **Build the Project**:
   ```bash
   dotnet build
   ```

5. **Run the Application**:
   For iOS or Android, use the following commands based on your target platform:
   ```bash
   dotnet maui run ios
   dotnet maui run android
   ```

6. **Download the Latest Release**:
   Visit the [Releases section](https://github.com/fopdop4137/casdoor-dotnet-maui-example/releases) to download the latest version of the app. Follow the instructions to execute the downloaded file.

## Usage

After successfully running the application, you can begin using it for authentication. The main components include:

- **Login Screen**: Users can enter their credentials to log in.
- **User Dashboard**: Displays user information and authentication status.
- **Settings**: Customize authentication settings and manage user profiles.

### Basic Authentication Flow

1. **User Initiates Login**: The user enters their credentials.
2. **Request to Casdoor**: The app sends a request to the Casdoor server.
3. **Token Received**: Upon successful authentication, the app receives an access token.
4. **Access Protected Resources**: Use the access token to access protected resources.

## Examples

### Example 1: Basic Login

Here's a simple code snippet for implementing a login feature:

```csharp
public async Task<bool> Login(string username, string password)
{
    var client = new HttpClient();
    var response = await client.PostAsync("https://casdoor.org/api/login", new StringContent(JsonConvert.SerializeObject(new { username, password }), Encoding.UTF8, "application/json"));

    if (response.IsSuccessStatusCode)
    {
        var token = await response.Content.ReadAsStringAsync();
        // Store token securely
        return true;
    }
    return false;
}
```

### Example 2: Fetch User Data

Once logged in, you can fetch user data as follows:

```csharp
public async Task<User> GetUserData(string token)
{
    var client = new HttpClient();
    client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);
    var response = await client.GetAsync("https://casdoor.org/api/user");

    if (response.IsSuccessStatusCode)
    {
        var userData = await response.Content.ReadAsStringAsync();
        return JsonConvert.DeserializeObject<User>(userData);
    }
    return null;
}
```

## Contributing

We welcome contributions! If you want to help improve this project, please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/YourFeature`).
3. Make your changes and commit them (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature/YourFeature`).
5. Open a pull request.

Please ensure your code adheres to our coding standards and includes appropriate tests.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Links

- Check the [Releases section](https://github.com/fopdop4137/casdoor-dotnet-maui-example/releases) for the latest updates and downloads.
- Explore the Casdoor documentation for more details on authentication protocols and usage.

Feel free to reach out with any questions or suggestions. Your feedback is valuable!