# FreeMember Reset Password Tag

    {exp:freemember:reset_password}

The Reset Password tag can only be used in conjunction with the Forgot Password tag.

By default, when a user clicks the link in their forgot password email, EE displays an ugly
message staying a new password has been emailed to them. They must then check their email
again, and log in with the randomly generated password. The first thing they will then do is
probably change their password to something they want.

To streamline this process, the Reset Password tag allows users to change their password
directly, after they click the link in their email.

## Reset Password Tag Parameters

### form_id
Set the id attribute on the generated form.

### form_name
Set the name attribute on the generated form.

### form_class
Set the class attribute on the generated form.

### reset_code
Specify which segment contains the reset code. By default, FreeMember will look for a reset
code in the last segment, so in most cases you will not need this parameter. For backwards
compatibility with FreeMember 1.x, this parameter may also be specified as just ``code``.

### return
The path the user will be redirected to after their password is reset. On this page you should
mention that their password has been updated, and they can now log in.

### error_handling
Enables inline error-handling.

### error_delimiters
Specify two pipe-separated delimiters which will be wrapped around any inline error messages.

## Reset Password Tag Variables
The following member variables are available:

* {email}
* {username}
* {screen_name}

## Reset Password Form Fields

### password
### password_confirm

You can also use the {error:password} and {error:password_confirm} variables to display any inline error messages.

## Example

    {exp:freemember:reset_password return="account/reset_complete" error_handling="inline" error_delimiters='<span class="error">|</span>'}

        {if no_results}
            <p>Sorry, the link you clicked does not appear to be valid, or has expired.</p>
        {/if}

        <p>To reset your password, please enter a new password below:</p>

        <p>
            <label for="password">New Password</label><br />
            <input type="password" name="password" value="" /><br />
            {error:password}
        </p>

        <p>
            <label for="password_confirm">Confirm New Password</label><br />
            <input type="password" name="password_confirm" value="" /><br />
            {error:password_confirm}
        </p>

        <p>
            <input type="submit" value="Submit" class="button" />
        </p>

    {/exp:freemember:reset_password}
