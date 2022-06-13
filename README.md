# Team-Worldwide-API-C#
Team Worldwide API C# .NET Client

Generated client from swagger 3 specification.  

## Example

            this.httpClient = new HttpClient();

            Client client = new Client(this.httpClient)
            {
                BaseUrl = this.apiUrl
            };

            this.statusTextBox.AppendText("Trying..." + client.BaseUrl + System.Environment.NewLine);

            try
            {

                Credentials credentials = new Credentials();
                credentials.Username = this.username;
                credentials.Password = this.password;

                await client.PostCredentialsItemAsync(credentials);

                this.statusTextBox.AppendText("Authenticated..." + System.Environment.NewLine);

                this.statusTextBox.AppendText("Getting statuses for " + this.houseBill + System.Environment.NewLine);

                Response4 response4 = await client.GetGetShipmentStatusCollectionAsync(this.houseBill, null);

                this.statusTextBox.AppendText("Got statuses" + System.Environment.NewLine);

                // @todo Rename Get_read16 object to Status or something more meaningful.  This is first version 
                // straight out of the oven.
                foreach (Get_read16 get_Read16 in response4.Hydra_member)
                {

                    this.statusTextBox.AppendText("Status Code: " + get_Read16.StatusCode + System.Environment.NewLine);

                    this.statusTextBox.AppendText(JsonConvert.SerializeObject(get_Read16) + System.Environment.NewLine);
                }


            } catch (Exception ex)
            {
                this.statusTextBox.AppendText(ex.Message);
            }
